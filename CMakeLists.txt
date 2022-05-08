# Ref:
# 1. https://stackoverflow.com/questions/35072473/executing-bash-commands-from-a-cmake-file
# 2. https://llvm.org/docs/tutorial/MyFirstLanguageFrontend/LangImpl08.html
# 3. https://llvm.org/docs/CMake.html

cmake_minimum_required(VERSION 3.19)
project(toy)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

find_package(LLVM REQUIRED CONFIG)

set(CMAKE_CXX_STANDARD 14)


#include_directories(/Users/tzuping/install/llvm/12.0.0/include)
#link_directories(/Users/tzuping/install/llvm/12.0.0/lib)
include_directories(${LLVM_INCLUDE_DIRS})
link_directories( ${LLVM_LIBRARY_DIRS} )
separate_arguments(LLVM_DEFINITIONS_LIST NATIVE_COMMAND ${LLVM_DEFINITIONS})
add_definitions(${LLVM_DEFINITIONS_LIST})
add_executable(toy main.cpp)

execute_process (
    COMMAND bash -c "/home/tzuping/install/llvm/14.0.3/bin/llvm-config --cxxflags --ldflags --system-libs --libs all"
    OUTPUT_VARIABLE outVar
)

message(STATUS "TT: ${outVar}")

llvm_map_components_to_libnames(llvm_libs
                                support
                                core
                                irreader
                                analysis
                                object
                                executionengine
                                scalaropts
                                instcombine
                                orcjit
                                runtimedyld
                                x86asmparser
                                amdgpuasmparser
                                armasmparser
                                avrasmparser
                                bpfasmparser
                                mipsasmparser
                                msp430asmparser
                                powerpcasmparser
                                riscvasmparser
                                sparcasmparser
                                systemzasmparser
                                webassemblyasmparser
                                aarch64asmparser
                                VEAsmParser)

# llvm_map_components_to_libnames(llvm_libs support core irreader ${outVar})


foreach(target ${LLVM_TARGETS_TO_BUILD})
    list(APPEND targets "LLVM${target}CodeGen")
endforeach()


target_link_libraries(toy ${llvm_libs} ${targets})

#LLVM_AsmParser