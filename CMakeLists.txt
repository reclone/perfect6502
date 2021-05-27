cmake_minimum_required(VERSION 3.0)

project (Perfect6502)

# Overall C compile flags
if (MSVC)
  set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /W3 /WX")
else()
  set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Werror -Wall -O3")
endif()

#add_subdirectory(apple1basic)
add_subdirectory(cbmbasic)

# Static library to include perfect6502 in other projects or executables
add_library(perfect6502 STATIC perfect6502.c netlist_sim.c)
target_include_directories(perfect6502 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

