
document submission for interim assessment:

- meeting notes
- interim report
- presentation video (< 15min)
- presentation file

Requirements of meeting notes:

4 sets of meeting notes in [Sep, Dec]

4 sets of meeting notes in [Jan, Apr]

does not go through Turnitin system.

- meeting discussion (supervisor’s feedback on project proposal)
- action points
- problem encountered

Requirement of interim report:

pdf format

- skeleton of final report.
- report progress in contributing to bigger project.

# TODO list


# Backlog

## 11.12

**Comments from Ken**:

You have identified some relevant works (e.g., [9][10]).

It'd be better to explain the limitations of these works in more detail.

For example, why generating KDVs can easily exceed GPU memory?

Please provide some numbers/calculations to explain this.

Can the dataset fit in the GPU memory or not?

You are suggested to plan for which functions will be demonstrated in Interim Presentation Video.

Needs exact number to explain GPU memory. explain which case will exceed GPU memory. need to show calculations. 

find out the reasons why. provide more details to tell the reasons. 

output graphics 可以找一些 lib. 

Experimental evaluation. 

baseline 可以先 visualize 出来先, tensor core 那些可以放到下一个 sem 去做. 

需要做一个 user manual -> 流程图, 即 state diagram. 

3 bandwidth options: rule of thumb; cross validation (fixed); adaptive
# GPU impl


# Related terminology

## study area
“**研究区域（Study Area）**”在核密度估计（Kernel Density Estimation, KDE）分析中扮演着至关重要的角色。根据您提供的命令行使用说明、文章描述以及源代码，以下是对“研究区域”的详细解释及其用途：

### **1. 研究区域的定义**

**研究区域**指的是进行点模式分析和核密度估计的地理空间范围。在您的程序中，研究区域通过一个掩模文件（**study area mask file**）来定义，这个文件通常是一个ASCII栅格文件（如`.asc`格式），其中每个栅格单元（cell）用特定的数值标识该单元是否属于研究区域。例如：

- **值为1**：表示该栅格单元在研究区域内。
- **值为NODATA（如-9999）**：表示该栅格单元不在研究区域内。

### **2. 研究区域在程序中的作用**

在源代码中，研究区域通过`AsciiRaster`结构体来表示，包含了栅格的列数、行数、左下角坐标、单元大小、无数据值以及栅格数据本身（`elements`数组）。程序在运行时会读取这个掩模文件，用于以下几个方面：

1. **限定计算范围**：
    - 仅在研究区域内进行密度估计，避免在不相关的区域进行不必要的计算，从而提高效率。
2. **边缘效应校正**：
    - **边缘效应**是指在研究区域边界附近，由于核函数（如高斯核）的计算涉及到区域外的空间，可能导致密度估计的不准确。为了解决这一问题，程序会计算每个样本点的**边缘校正因子**，即核函数在研究区域内的质量（mass）。这个过程依赖于研究区域的边界信息，以确保边缘附近的点密度估计更为准确。
3. **优化计算**：
    - 通过标记研究区域的边界，程序可以在计算距离和密度时优化搜索范围。例如，只有那些距离边界较近的点才需要进行额外的边缘效应校正，这减少了不必要的计算负担。

**研究区域**在您的程序中主要用于：

- **限定分析范围**：确保核密度估计只在感兴趣的地理区域内进行。
- **边缘效应校正**：通过边界信息，调整边缘附近点的密度估计，提升结果的准确性。
- **优化计算效率**：通过掩模文件的使用，减少不必要的计算，提高整体程序的运行效率。


根据提供的源代码和研究区域的描述，`maskSim160000.asc` 文件的主要作用如下：

1. **定义研究区域的空间范围**：
    
    - 文件中的栅格数据（即 400 × 400 个 0）表示所有栅格单元均属于研究区域。具体来说：
        - **值为 0**：表示该栅格单元在研究区域内。
        - **值为 -9999（NODATA）**：表示该栅格单元不在研究区域内。
    - 由于所有栅格单元的值均为 **0**，意味着整个 400 × 400 的网格区域都是研究区域，没有任何区域被排除。
2. **限定计算范围**：
    
    - 在核密度估计（KDE）分析中，程序会根据该掩模文件仅在研究区域内进行密度计算，避免在非研究区域进行无意义的计算，从而提高计算效率。
3. **边缘效应校正**：
    
    - 源代码中的 `MarkBoundary` 函数会根据掩模文件标记研究区域的边界单元。边界单元在后续的密度估计中用于校正边缘效应，确保在研究区域边界附近的点密度估计更加准确。
4. **优化计算效率**：
    
    - 通过掩模文件标记边界和内部单元，程序可以优化在计算距离和密度时的搜索范围，仅对需要进行边缘校正的点进行额外计算，从而减少不必要的计算负担。
栅格数据本身的值不是NODATA就说明是我们的研究区域:

通过 `MarkBoundary` 函数，将研究区域的边界单元标记为 **1.0f**，内部单元保持为 **0.0f**
![[Pasted image 20250106234301.png]]


![[Pasted image 20250106235301.png]]


## Edge Correction
边缘效应校正（Edge Correction）是在空间点模式分析中，用于纠正由于研究区域边界导致的估计偏差的方法。具体来说，当我们使用核密度估计（Kernel Density Estimation, KDE）来估计空间点的密度时，位于研究区域边界附近的样本点其核函数（例如圆形核）的一部分可能会超出研究区域。这种情况会导致边界附近的密度估计值被低估，因为部分核质量没有被考虑在内。

### 边缘效应校正的基本原理

1. **核质量不完全**：对于靠近边界的样本点，其核函数的一部分位于研究区域之外，因此实际在研究区域内的核质量小于完整核质量。
    
2. **权重调整**：为了纠正这一偏差，边缘效应校正通过为每个样本点分配一个权重来补偿核质量的缺失。这个权重通常是研究区域内核质量的倒数，即：

![[Pasted image 20250106235434.png]]

这样，边界附近的样本点由于核质量减少，其权重会增大，从而在密度估计中得到适当的补偿。
### 实现过程

根据您提供的代码和描述，边缘效应校正的实现过程大致如下：

1. **计算样本点到边界的距离**（`CalcDist2Boundary`函数）：
    
    - 对于每个样本点，计算其到研究区域边界的最近距离。这一步骤可以在GPU或CPU上进行加速计算。
    - 距离的计算基于栅格（`AsciiRaster`）数据，识别边界单元格并计算点到这些单元格的最小距离。
2. **计算边缘校正权重**（`EdgeCorrectionWeightsExact`函数）：
    
    - 对于每个样本点，根据其到边界的距离和当前带宽（`h`）值，判断是否需要进行校正。
        
    - 如果样本点距离边界足够远（例如，距离大于某个阈值，如`CUT_OFF_FACTOR * h²`），则认为其核质量完全位于研究区域内，权重设为1.0，无需校正。
        
    - 对于靠近边界的样本点，计算其核质量在研究区域内的实际比例。这通常通过在研究区域内积分核函数来实现，例如使用高斯核函数（`GaussianKernel`）与栅格单元面积相乘并累加。
        
    - 最终，权重为上述核质量比例的倒数，即：
![[Pasted image 20250107000807.png]]
    -  这些权重随后用于调整密度估计，以补偿边缘效应带来的偏差。

## GaussianKernel
float h2 = h * h;
![[Pasted image 20250107001319.png]]


![[Pasted image 20250107001540.png]]

![[Pasted image 20250107002311.png]]
![[Pasted image 20250107002426.png]]
![[Pasted image 20250107002451.png]]




## kd-tree


## density (output)

![[Pasted image 20250107105923.png]]

![[Pasted image 20250107105715.png]]

### step 1: CalcEdgeCorrectionWeights
![[Pasted image 20250107113306.png]]
### step 2: DensityAtPointsKdtr
![[Pasted image 20250107113342.png]]

### step 3: dCopyDensityValues
![[Pasted image 20250107113623.png]]
![[Pasted image 20250107113908.png]]

![[Pasted image 20250107113523.png]]
![[Pasted image 20250107113947.png]]
![[Pasted image 20250107113952.png]]