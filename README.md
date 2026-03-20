# llvm-build

This project provides binary builds of LLVM, for major platforms. We build LLVM using a GitHub Action, and then publish binaries as archives to a GitHub Release.

## Motivation

These builds could be useful if you are developing a compiler. For example, you might be using the Rust library [Inkwell](https://thedan64.github.io/inkwell/).

Compiling LLVM from source takes a long time. It is faster in your compiler’s CI pipeline to build against existing LLVM binaries.

LLVM publishes official binaries. However, the main official binaries are [targeted at users who want an LLVM toolchain](https://github.com/llvm/llvm-project/issues/53052#issuecomment-1723217620), and not compiler writers who want to link against LLVM. As such, those binary archives are missing key components such as llvm-config.

Finally, across all platforms, we publish artifacts using the same archive format and file extension (`.tar.zst`). This makes unarchiving the files marginally more consistent and straightforward.

## Scope

In addition to the core LLVM libraries, we build LLD.

Binaries which run on x86-64 are built for both GNU/Linux and Windows. Binaries which run on ARM64 are built for macOS.

We enable the following targets for code generation: AArch64 (ARM64) and X86 (which includes x86-64).
