cmake_minimum_required(VERSION 3.10)

project(imgui VERSION 0.0.0)

add_compile_options("$<$<C_COMPILER_ID:MSVC>:/utf-8>")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

# Generate files for clangd to use.
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON CACHE INTERNAL "")

# -- library ----------------------------------------------------------------

set(SRC_IMGUI
    "imconfig.h"
    "imgui.h"
    "imgui_internal.h"
    "imstb_rectpack.h"
    "imstb_textedit.h"
    "imstb_truetype.h"
    "imgui.cpp"
    "imgui_demo.cpp"
    "imgui_draw.cpp"
    "imgui_tables.cpp"
    "imgui_widgets.cpp"
)
set(SOURCES
    ${SRC_IMGUI}
)
source_group("imgui" FILES ${SRC_IMGUI})

add_library(imgui ${SOURCES})
target_include_directories(imgui PUBLIC ".")
target_compile_features(imgui PUBLIC cxx_std_17)
