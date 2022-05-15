# llvm_toy

<br>
1. Compile llvm lib command<br>
<br>
==> cmake -S llvm -B build -G "Unix Makefiles" -DLLVM_ENABLE_PROJECTS='clang;clang-tools-extra;cross-project-tests;flang;libclc;lld;lldb;mlir;openmp;polly;pstl'  -DLLVM_ENABLE_RUNTIMES='libcxx;libcxxabi;libunwind;compiler-rt;libc' -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/home/tzuping/install/llvm/14.0.3<br>
<br>
==> cd build && make -j4<br>
<br>

<br>
2. Build application for llvm lib<br>
<br>
mkdir build<br>
<br>
cd build<br>
<br>
cmake -DLLVM_TARGETS_TO_BUILD="all"  -DCMAKE_C_COMPILER=/usr/local/opt/llvm/bin/clang -DCMAKE_CXX_COMPILER=/usr/local/opt/llvm/bin/clang++ -DLLVM_DIR=/usr/local/opt/llvm/lib/cmake/llvm/ ../<br>
<br>
or<br>
<br>
cmake -DLLVM_TARGETS_TO_BUILD="all" -DCMAKE_C_COMPILER=/home/tzuping/install/llvm/12.0.1/bin/clang -DCMAKE_CXX_COMPILER=/home/tzuping/install/llvm/12.0.1/bin/clang++ -DLLVM_DIR=/home/tzuping/install/llvm/12.0.1/lib/cmake/llvm/ ../
<br>
<br>
make<br>
<br>
(only for CLion Test)
