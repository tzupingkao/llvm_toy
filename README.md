# llvm_toy

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
