﻿# 
# Copyright(c) 2018 Intel Corporation
# SPDX - License - Identifier: BSD - 2 - Clause - Patent
# 

# ASM_SSE2 Directory CMakeLists.txt

# Include Encoder Subdirectories
include_directories (${PROJECT_SOURCE_DIR}/Source/API/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/Codec/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/C_DEFAULT/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/ASM_SSE2/)
include_directories (${PROJECT_SOURCE_DIR}/Source/Lib/VPX/)

if(CMAKE_C_COMPILER_ID STREQUAL "GNU")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -msse2")
endif()

if(CMAKE_C_COMPILER_ID STREQUAL "Intel")
    SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC -static-intel -w")
endif()

if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /MP")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /MP")   
endif(MSVC)


file(GLOB all_files
    "*.h"
    "*.c"
    "*.asm"
)

add_library(ASM_SSE2 STATIC
       ${all_files}
)



