cmake_minimum_required(VERSION 3.10)
project(SuperIDE)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# SDL2
add_subdirectory(thirdparty/sdl2)

# ImGui
add_library(imgui
    thirdparty/imgui/imgui.cpp
    thirdparty/imgui/imgui_draw.cpp
    thirdparty/imgui/imgui_widgets.cpp
    thirdparty/imgui/imgui_tables.cpp
    thirdparty/imgui/backends/imgui_impl_sdl2.cpp
    thirdparty/imgui/backends/imgui_impl_opengl3.cpp
)

target_include_directories(imgui PUBLIC thirdparty/imgui)

add_executable(superide
    src/main.cpp
)

target_link_libraries(superide PRIVATE SDL2-static imgui)
