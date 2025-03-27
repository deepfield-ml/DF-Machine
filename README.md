# DF Machine (Experimental Go Modification)

**⚠️ THIS IS AN MODIFIED VERSION OF THE OFFICIAL GO PROGRAMMING LANGUAGE ⚠️**

This repository contains **DF Machine**, a modified version of Go (currently based on Go 1.24.0) focused on exploring potential optimizations for data analysis and machine learning workloads, and specialized inter-language communication.

**It includes non-standard changes to the compiler and runtime and may produce different results (especially for floating-point math) or exhibit different performance characteristics compared to official Go.** Use with caution and primarily for research or experimentation.

For the official Go project, please visit [https://github.com/golang/go](https://github.com/golang/go) or [https://go.dev/](https://go.dev/).

## Licensing

DF Machine is based on the Go programming language, which is licensed under a BSD-style license. See the [LICENSE](LICENSE) file for the full terms governing the original code.

Modifications made specifically for DF Machine (Copyright 2025 Gordon.H | Deepfield ML) are also released under the same BSD-style license.
![Gopher image](https://golang.org/doc/gopher/fiveyears.jpg)
*Gopher image by [Renee French][rf], licensed under [Creative Commons 4.0 Attribution license][cc4-by].*

Our canonical Git repository is located at https://go.googlesource.com/go.
There is a mirror of the repository at https://github.com/golang/go.

Unless otherwise noted, the Go source files are distributed under the
BSD-style license found in the LICENSE file.

## DF Machine Modifications (Summary)

This version includes the following experimental changes compared to the base Go version it was forked from:

*   **Compiler (`cmd/compile`):**
    *   Disabled `x + 0 -> x` optimization rule (AMD64).
    *   Disabled specific `Neg64F`/`Neg32F` floating-point negation optimization rule (AMD64).
    *   Removed heuristic check (`useFMA`) for FMA (Fused Multiply-Add) instruction generation, potentially using FMA more aggressively (AMD64). **Warning:** This *will* change floating-point results.
*   **Runtime (`runtime`):**
    *   Hardcoded GC trigger percentage to behave like `GOGC=200`, potentially reducing GC frequency at the cost of higher peak memory usage and potentially longer pauses. (Modified `mgcpacer.go` for 1.24.0).
    *   Minor change to `sweepMinHeapDistance` constant (Illustration).
    *   Added debug print statements during GC phases.

*(Keep this list updated as you make more significant changes)*

### Download and Install

#### Binary Distributions


### Contributing

Go is the work of thousands of contributors. We appreciate your help!

To contribute, please read the contribution guidelines at https://go.dev/doc/contribute.

Note that the Go project uses the issue tracker for bug reports and
proposals only. See https://go.dev/wiki/Questions for a list of
places to ask questions about the Go language.

[rf]: https://reneefrench.blogspot.com/
[cc4-by]: https://creativecommons.org/licenses/by/4.0/
