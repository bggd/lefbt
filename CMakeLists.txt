cmake_minimum_required(VERSION 3.1)

set(CMAKE_INSTALL_PREFIX ${CMAKE_SOURCE_DIR}/thirdparty CACHE PATH "..." FORCE)

project(prebuild C CXX)

find_package(OPENGL REQUIRED)

add_subdirectory(thirdparty/glfw)

add_library(imgui
  thirdparty/imgui/imgui.cpp
  thirdparty/imgui/imgui_draw.cpp
  thirdparty/imgui/imgui_widgets.cpp
  thirdparty/imgui/imgui_demo.cpp
  thirdparty/imgui/examples/imgui_impl_opengl2.cpp
  thirdparty/imgui/examples/imgui_impl_glfw.cpp
)

target_include_directories(imgui PRIVATE thirdparty/imgui)
target_link_libraries(imgui OpenGL::GL glfw)

install(TARGETS imgui)
