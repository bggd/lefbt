cmake_minimum_required(VERSION 3.1)

set(CMAKE_INSTALL_PREFIX ${CMAKE_SOURCE_DIR}/thirdparty CACHE PATH "..." FORCE)

project(prebuild C CXX)

find_package(OPENGL REQUIRED)

set(GLFW_BUILD_DOCS OFF)
set(GLFW_BUILD_TESTS OFF)
set(GLFW_BUILD_EXAMPLES OFF)
add_subdirectory(glfw)

add_library(imgui
  imgui/imgui.cpp
  imgui/imgui_draw.cpp
  imgui/imgui_widgets.cpp
  imgui/imgui_demo.cpp
  imgui/examples/imgui_impl_opengl2.cpp
  imgui/examples/imgui_impl_glfw.cpp
)

target_include_directories(imgui PRIVATE imgui)
target_link_libraries(imgui OpenGL::GL glfw)

install(TARGETS imgui)
