cmake_minimum_required(VERSION 3.0)

configure_file(cbmbasic.bin ${CMAKE_CURRENT_BINARY_DIR}/cbmbasic.bin COPYONLY)

if (NOT MSVC)
  # Commodore BASIC test executable is POSIX
  add_executable(cbmbasic cbmbasic.c runtime.c runtime_init.c plugin.c console.c emu.c readdir.c)
  target_link_libraries(cbmbasic perfect6502)
  
  # Warnings in test executable code - gross!
  target_compile_options(cbmbasic PRIVATE -Wno-unused-but-set-variable -Wno-unused-result)
endif()