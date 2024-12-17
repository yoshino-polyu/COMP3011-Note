# [What does -G flag do exactly?](https://forums.developer.nvidia.com/t/what-does-g-flag-do-exactly/256174)
See [here](https://docs.nvidia.com/cuda/cuda-compiler-driver-nvcc/index.html#device-debug-g). It is intended to generate device-debuggable code. Most optimizations that the compiler might do are disabled. Furthermore, additional symbol information (similar to `-lineinfo`) is included in the fatbinary.

Device machine code generation ends up being quite different, in my experience. A kernel compiled with `-G` will usually have noticeably more machine instructions in it than the same one without.

It’s difficult to say exactly what the `-G` option “does” that could cause that behavior, beyond what you see above. There are a few possible cases:

- There is a bug in your code, and optimization tends to make it more visible.
- There is a bug in the compiler that manifests during optimization.

It’s impossible to say which with no code.

You might try updating to the latest toolchain, if you’re not already there. Bugs get fixed all the time. Also, NaN’s are fairly easy to detect. If you have a sequence of calculations, with data flowing from one step to the next, [it’s not difficult to detect NaN](https://forums.developer.nvidia.com/t/function-only-works-correctly-with-cuda-8-0-in-release-mode/48553/20?page=2) in between steps in the sequence although it typically requires additional debug code. Identifying the step in the sequence that converts “ordinary” data to NaN may be a useful debug or localization strategy.




Nice to contact with you!

Attached pls find RDP generic inspection checklist for your reference and study again, you can good quality control in production and package line accordingly. please especial for the below points:

1. All RDP item must be passed the carton drop test and transport test. and for this project item, the individual package also need to passed **special drop test**, the detail see attached file.
2. As this project item is collection item, and have high value, the quality must be perfect, so you must be do 100% full check all products, to ensure product quality. and send your **full inspection report** to us for record.
3. Please let us know once you start to production, we will arrange our colleague to in line check.

Please feel free contact with us if you have problem, thank you for your cooperation and support!

Kind Regards,

