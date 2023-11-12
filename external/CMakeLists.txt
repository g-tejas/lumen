set(GLFW_BUILD_EXAMPLES OFF CACHE INTERNAL "Build the GLFW example programs")
set(GLFW_BUILD_TESTS OFF CACHE INTERNAL "Build the GLFW test programs")
set(GLFW_BUILD_DOCS OFF CACHE INTERNAL "Build the GLFW documentation")
set(GLFW_INSTALL OFF CACHE INTERNAL "Generate installation target")

set(GUI_SOURCES
  "glad/src/glad.c"
  "imgui/imgui.cpp"
  "imgui/imgui_demo.cpp"
  "imgui/imgui_draw.cpp"
  "imgui/imgui_tables.cpp"
  "imgui/imgui_widgets.cpp"
  "imgui/backends/imgui_impl_glfw.cpp"
  "imgui/backends/imgui_impl_opengl3.cpp"
  "implot/implot.cpp"
  "implot/implot_items.cpp"
  "implot/implot_demo.cpp"
  )

find_package(OpenGL REQUIRED)
add_subdirectory("glfw")

add_library(gui STATIC ${GUI_SOURCES})

target_include_directories(gui PUBLIC
  "${CMAKE_CURRENT_SOURCE_DIR}/glad/include"
  "${CMAKE_CURRENT_SOURCE_DIR}/imgui"
  "${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends/"
  "${CMAKE_CURRENT_SOURCE_DIR}/implot"
  "${CMAKE_CURRENT_SOURCE_DIR}/imgui-command-palette"
  )

target_link_libraries(gui PUBLIC glfw OpenGL::GL)
