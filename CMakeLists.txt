cmake_minimum_required(VERSION 3.0)

project (Perfect6502)

# Overall C compile flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Werror -Wall -O3")

# Static library to include perfect6502 in other projects or executables
add_library(perfect6502 STATIC perfect6502.c netlist_sim.c)
target_include_directories(perfect6502 PUBLIC ${CMAKE_CURRENT_BINARY_DIR})

# Commodore BASIC test executable
add_executable(cmbasic cbmbasic.c runtime.c runtime_init.c plugin.c console.c emu.c)
target_link_libraries(cmbasic perfect6502)
# Warnings in test executable code - gross!
target_compile_options(cmbasic PRIVATE -Wno-unused-but-set-variable -Wno-unused-result)