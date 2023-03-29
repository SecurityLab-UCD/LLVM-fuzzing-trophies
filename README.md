# LLVM-fuzzing-trophies

- &#x2714;: Compiled successfully.
- &#x23F3;: Compiler timed out, possibly infinite recursion
- &#x274C;: Compiler crashed due to a bug or assertion
- &#x1F6A7;: Compiler crashed due to missing features
- &#x26A0;: Compiler didn't crash, but misbehaved

| Issue #                                                    | Description                                                                                                                                     |                                    Fixing commit                                    | Upstream  |  LLVM 15  |  LLVM 14  |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------: | :-------: | :-------: | :-------: |
| LLVM                                                       |                                                                                                                                                 |                                                                                     |           |           |           |
| [57251](https://github.com/llvm/llvm-project/issues/57251) | `DAGTypeLegalizer::RemapId` infinite recursion on AArch64, X86, and AIE.                                                                        |                                          -                                          | &#x23F3;  | &#x23F3;  | &#x23F3;  |
| [57452](https://github.com/llvm/llvm-project/issues/57452) | Codegen SExt index value of `extractelement`, translating `i1 true` into `i32 -1`.                                                              | [c2e7c9cb33ac](https://reviews.llvm.org/rGc2e7c9cb33acbd118fe5011a1607d6cf8e21de34) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57658](https://github.com/llvm/llvm-project/issues/57658) | Infinite recursion in `VectorLegalizer::LegalizeOp`.                                                                                            | [545affbf79bf](https://reviews.llvm.org/rG545affbf79bfbc19659a0f442f22558791aa4404) | &#x2714;  | &#x23F3;  | &#x23F3;  |
| [58511](https://github.com/llvm/llvm-project/issues/58511) | Infinite recursion in `foldBinOpIntoSelect`.                                                                                                    | [00816714f965](https://reviews.llvm.org/rG00816714f96505c59c236f3f0fd2eb815c57f674) | &#x2714;  | &#x23F3;  | &#x23F3;  |
| [58538](https://github.com/llvm/llvm-project/issues/58538) | `CodeGenPrepare` infinitely sinking `cmp`.                                                                                                      |                                          -                                          | &#x23F3;  | &#x23F3;  | &#x23F3;  |
| [58580](https://github.com/llvm/llvm-project/issues/58580) | SimplifyCFG infinite recursion assertion failed                                                                                                 |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58583](https://github.com/llvm/llvm-project/issues/58583) | IR Verifier didn't check if switch case is constant                                                                                             | [348189880b7b](https://reviews.llvm.org/rG348189880b7bc9513ccdd0ea3a1e255b4d3190e7) | &#x2714;  | &#x26A0;  | &#x26A0;  |
| [59055](https://github.com/llvm/llvm-project/issues/59055) | [AsmPrinter] Global Constant with Big Endian crashes backend with assertion `ShiftAmt <= BitWidth && "Invalid shift amount"` failed             | [fc1ffb4c0ea8](https://reviews.llvm.org/rGfc1ffb4c0ea886bf37a2169db3d9270eb600d9fc) | &#x274C;  | &#x274C;  | &#x274C;  |
| [59316](https://github.com/llvm/llvm-project/issues/59316) | [Transforms] LowerSwitch tries to get sext on i128, causing an assertion error.                                                                 | [1db51d8eb2d2](https://reviews.llvm.org/rG1db51d8eb2d220a4f0000555ada310990098cf5b) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59515](https://github.com/llvm/llvm-project/issues/59515) | [ADT] APSInt::getExtValue() - assumes signed bounds                                                                                             |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| AArch64                                                    |                                                                                                                                                 |                                                                                     |           |           |           |
| [57282](https://github.com/llvm/llvm-project/issues/57282) | Double free given invalid index in `insertelement`                                                                                              | [3dd861818a68](https://reviews.llvm.org/rG3dd861818a68b2e0b21d426ee956ec8d69f89c88) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57326](https://github.com/llvm/llvm-project/issues/57326) | SelectionDAG uses uninitialized array and have OOB Write given long `shuffelvector` mask.                                                       | [2343ad755d60](https://reviews.llvm.org/rG2343ad755d602fe67e3418d4edf0a5d0780045d6) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58050](https://github.com/llvm/llvm-project/issues/58050) | `fcmp true / false` used in `and` / `or` branching condition causes crash `Unknown FP condition!`                                               |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58156](https://github.com/llvm/llvm-project/issues/58156) | GlobalIsel unable to legalize vectorized binaryop(`G_ADD`, `G_SUB`, ...)                                                                        | [2343ad755d60](https://reviews.llvm.org/rG90c98f8e5516901cd5dbd677e65fb8d7dd483cba) | &#x2714;  | &#x1F6A7; | &#x1F6A7; |
| [58211](https://github.com/llvm/llvm-project/issues/58211) | GlobalIsel unable to translate `ret` with `v1i8 / v1i16`                                                                                        |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58274](https://github.com/llvm/llvm-project/issues/58274) | GlobalIsel cannot select `G_ZEXT` / `G_SEXT` / `G_ANYEXT` with `v2i16`                                                                          |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58350](https://github.com/llvm/llvm-project/issues/58350) | Storing a `v1f32` along with a `f32` causes assertion error "Extract subvector index must be a constant"                                        | [c1909d73372e](https://reviews.llvm.org/rGc1909d73372e669a44a2aefe82de873c2161cc44) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58615](https://github.com/llvm/llvm-project/issues/58615) | Passing a v1f32 arg through memory crashes backend with "Invalid TRUNCATE!" assertion error                                                     | [ef0d689e8be2](https://reviews.llvm.org/rGef0d689e8be2ac22b2e2da477217c761354c0ff9) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59647](https://github.com/llvm/llvm-project/issues/59647) | [AArch64] `srem` with vector of -1's crashes backend when targeting Cortex A710                                                                 | [c9602e02fc16](https://reviews.llvm.org/rGc9602e02fc16e8a3fcb6f7b58d8615b04a8fde38) | &#x2714;  | &#x274C;  | &#x274C;  |
| AMDGPU                                                     |                                                                                                                                                 |                                                                                     |           |           |           |
| [57406](https://github.com/llvm/llvm-project/issues/57406) | GlobalIsel `AMDGPUPreLegalizerCombiner` double frees on negative index.                                                                         | [8901f7cebc73](https://reviews.llvm.org/rG8901f7cebc73383d0cda19a870ffe410a67653e9) | &#x2714;  | &#x274C;  | &#x274C;  |
| [57408](https://github.com/llvm/llvm-project/issues/57408) | GlobalIsel `legalizeExtractVectorElt` crashes on negative index.                                                                                | [8901f7cebc73](https://reviews.llvm.org/rG8901f7cebc73383d0cda19a870ffe410a67653e9) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58171](https://github.com/llvm/llvm-project/issues/58171) | Allocating large mumber of `bool`s on stack causes "Register number out of range"                                                               |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58210](https://github.com/llvm/llvm-project/issues/58210) | No registers from class available to allocate for R600 / Cannot select for AMDGCN                                                               |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58331](https://github.com/llvm/llvm-project/issues/58331) | `mul` `v1i8` / `v1i16` causes crash during IR optimizations due to type mismatch                                                                | [838fd611b79e](https://reviews.llvm.org/rG838fd611b79e3514eead5dd724140df046172ef1) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58861](https://github.com/llvm/llvm-project/issues/58861) | [AMDGPU] `SI annotate control flow` pass failed with error `failed to annotate CFG`                                                             | [4bbcbdaee5c9](https://reviews.llvm.org/rG4bbcbdaee5c937b17baaf04357383c8b15d408f2) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59313](https://github.com/llvm/llvm-project/issues/59313) | [AMDGCN] can't select fpow when the second arg is non-constant                                                                                  |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| ARM                                                        |                                                                                                                                                 |                                                                                     |           |           |           |
| [59317](https://github.com/llvm/llvm-project/issues/59317) | [ARM] IselLowering unsigned overflow to crash using APInt in PerformSHLSimplify                                                                 | [ee31a4a7029f](https://reviews.llvm.org/rGee31a4a7029f2f6fda5f416e7eb67ca3907d9e36) | &#x2714;  | &#x274C;  | &#x274C;  |
| BPF                                                        |                                                                                                                                                 |                                                                                     |           |           |           |
| [58884](https://github.com/llvm/llvm-project/issues/58884) | Vector used across basic block causes assertion `LHS.getValueType().isVector() == VT.isVector() && "Cannot compare scalars to vectors"` to fail |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| Hexagon                                                    |                                                                                                                                                 |                                                                                     |           |           |           |
| [59009](https://github.com/llvm/llvm-project/issues/59009) | Cannot handle call operand v8i1                                                                                                                 |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [59042](https://github.com/llvm/llvm-project/issues/59042) | i1 vector crashes backend with error `Not a vector MVT!`                                                                                        | [534b26aa0767](https://reviews.llvm.org/rG534b26aa07675d7c4b579b1179e07ddf5e880d17) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59044](https://github.com/llvm/llvm-project/issues/59044) | Cannot select `mulhu` for v4i8 and v2i16                                                                                                        | [ea6693d4c840](https://reviews.llvm.org/rGea6693d4c840272b5f9b83518b474ed7b2449744) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59077](https://github.com/llvm/llvm-project/issues/59077) | Cannot select `select` for v2i32                                                                                                                | [4bb6e220a002](https://reviews.llvm.org/rG4bb6e220a002ab23e835a28364fdf071ef87d0d5) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59663](https://github.com/llvm/llvm-project/issues/59663) | Cannot select `vselect` for v8i1                                                                                                                |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [59685](https://github.com/llvm/llvm-project/issues/59685) | Cannot select `truncate` for i1 vectors                                                                                                         |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| NVPTX                                                      |                                                                                                                                                 |                                                                                     |           |           |           |
| [57398](https://github.com/llvm/llvm-project/issues/57398) | SelectionDAG Cannot select `dynamic_stackalloc`                                                                                                 |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [57404](https://github.com/llvm/llvm-project/issues/57404) | SelectionDAG Cannot select `mul i1`                                                                                                             |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [57405](https://github.com/llvm/llvm-project/issues/57405) | SelectionDAG Cannot select `setcc`                                                                                                              |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58305](https://github.com/llvm/llvm-project/issues/58305) | Assertion `CastInst::castIsValid(opc, C, Ty) && "Invalid constantexpr cast!"` failed                                                            |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58428](https://github.com/llvm/llvm-project/issues/58428) | `icmp i1` used as branching condition crashes backend                                                                                           |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [59179](https://github.com/llvm/llvm-project/issues/59179) | Global of non-standard type causes assertion error in debug build and memory corruption in release build                                        |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [59742](https://github.com/llvm/llvm-project/issues/59742) | [NVPTX] Assembly printer didn't implement `MCBinaryExpr::And`                                                                                   |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| PowerPC                                                    |                                                                                                                                                 |                                                                                     |           |           |           |
| [59074](https://github.com/llvm/llvm-project/issues/59074) | Backend crash due to index out of bound when `lshr` / `shl` i128 vector after `sub`                                                             |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| RISCV                                                      |                                                                                                                                                 |                                                                                     |           |           |           |
| [58025](https://github.com/llvm/llvm-project/issues/58025) | Copying a `v1f32` vector between blocks causes assertion error "Invalid `ANY_EXTEND`"                                                           | [12357e88af66](https://reviews.llvm.org/rG12357e88af669b00a5c4c607b93b716a6c474846) | &#x2714;  | &#x274C;  | &#x274C;  |
| [58027](https://github.com/llvm/llvm-project/issues/58027) | Cannot scavenge register without an emergency spill slot                                                                                        | [4554663bc0da](https://reviews.llvm.org/rG4554663bc0da71d61ab488641c95ef98430cb451) | &#x2714;  | &#x274C;  | &#x274C;  |
| VE                                                         |                                                                                                                                                 |                                                                                     |           |           |           |
| [58994](https://github.com/llvm/llvm-project/issues/58994) | `udiv` / `urem` crashes backend with assertion `LHS.getValueType().isVector() == VT.isVector() && "Cannot compare scalars to vectors"` failed   | [fe05a0a3ddbf](https://reviews.llvm.org/rGfe05a0a3ddbf7fb54af9536331d39b138763e17a) | &#x2714;  | &#x274C;  | &#x274C;  |
| WASM                                                       |                                                                                                                                                 |                                                                                     |           |           |           |
| [58904](https://github.com/llvm/llvm-project/issues/58904) | Assertion `isReg() && "This is not a register operand!"` failed during pass `Machine Common Subexpression Elimination` (Regression)             | [629f17c51637](https://reviews.llvm.org/rG629f17c5163762852db03581f187cf3b082a2a34) | &#x2714;  | &#x2714;  | &#x2714;  |
| [59625](https://github.com/llvm/llvm-project/issues/59625) | v1i8 / v1i16 crashes backend with invalid Bitcast when targeting `bleeding-edge`                                                                | [00eef4f7c384](https://reviews.llvm.org/rG00eef4f7c384456e0df8f855b99eab384a213c23) | &#x2714;  | &#x274C;  | &#x274C;  |
| [59626](https://github.com/llvm/llvm-project/issues/59626) | Backend crash with "Unexpected all-undef build_vector" when targeting `bleeding-edge`                                                           | [f841ad30d77e](https://reviews.llvm.org/rGf841ad30d77eeb4c51663e68efefdb734c7a3d07) | &#x2714;  | &#x274C;  | &#x274C;  |
| X86                                                        |                                                                                                                                                 |                                                                                     |           |           |           |
| [57283](https://github.com/llvm/llvm-project/issues/57283) | SelectionDAG assertion failure on shift                                                                                                         | [5377abcde240](https://reviews.llvm.org/rG5377abcde2409dc066b4b9e3425900df1eff927e) | &#x2714;  | &#x2714;  | &#x274C;  |
| [57474](https://github.com/llvm/llvm-project/issues/57474) | SelectionDAG assertion failure on shift                                                                                                         | [eaede4b5b7cf](https://reviews.llvm.org/rGeaede4b5b7cfc13ca0e484b4cb25b2f751d86fd9) | &#x2714;  | &#x2714;  | &#x274C;  |
| [59318](https://github.com/llvm/llvm-project/issues/59318) | [CodeGen] Backend crash with machine code errors                                                                                                |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58455](https://github.com/llvm/llvm-project/issues/58455) | Assertion "Can't handle this yet!" failed when scheduling                                                                                       |                                          -                                          | &#x1F6A7; | &#x1F6A7; | &#x1F6A7; |
| [58924](https://github.com/llvm/llvm-project/issues/58924) | Backend crash during pass `X86 FP Stackifier`                                                                                                   |                                          -                                          | &#x274C;  | &#x274C;  | &#x274C;  |
| [58628](https://github.com/llvm/llvm-project/issues/59628) | Cannot select `X86ISD::VZEXT_MOVL` when targeting Intel Sapphire Rapids                                                                         | [1cbcd8ad2071](https://reviews.llvm.org/rG1cbcd8ad2071178e9bb7c0c6b58a19c1283db9e3) | &#x2714;  | &#x274C;  | &#x274C;  |
| XCore                                                      |                                                                                                                                                 |                                                                                     |           |           |           |
| [D137124](https://reviews.llvm.org/D137124)                | Register null MCTargetStreamer to fix null dereference when printing globals                                                                    | [3bb12d3005ff](https://reviews.llvm.org/rG3bb12d3005ffdf5b2b34d4a84008e50ef4577e46) | &#x2714;  | &#x2714;  | &#x2714;  |
