
# This file is a part of Simple-XX/SimpleKernel (https://github.com/Simple-XX/SimpleKernel).
#
# CMakeLists.txt for Simple-XX/SimpleKernel.

PROJECT(arch CXX ASM)

find_asm_source_files(boot_asm_src ${arch_SOURCE_DIR}/boot)
set(boot_src ${boot_asm_src})

aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/port port_cpp_src)
set(port_src ${port_cpp_src})

set(arch_src ${boot_src} ${port_src})

add_library(${PROJECT_NAME} OBJECT ${arch_src})

target_include_libc_header_files(${PROJECT_NAME})
target_include_arch_header_files(${PROJECT_NAME})
target_include_common_header_files(${PROJECT_NAME})
