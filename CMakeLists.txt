cmake_minimum_required(VERSION 3.4...3.20 FATAL_ERROR)

project(IMGUI VERSION 3.4.0 LANGUAGES C)

add_library(imgui "${IMGUI_SOURCE_DIR}/backends/imgui_impl_glfw.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_glfw.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3_loader.h"
                 "${IMGUI_SOURCE_DIR}/misc/cpp/imgui_stdlib.h"
                 "${IMGUI_SOURCE_DIR}/misc/cpp/imgui_stdlib.cpp"
                 "${IMGUI_SOURCE_DIR}/imconfig.h"
                 "${IMGUI_SOURCE_DIR}/imgui.h"
                 "${IMGUI_SOURCE_DIR}/imgui.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_demo.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_draw.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_internal.h"
                 "${IMGUI_SOURCE_DIR}/imgui_tables.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_widgets.cpp"
                 "${IMGUI_SOURCE_DIR}/imstb_rectpack.h"
                 "${IMGUI_SOURCE_DIR}/imstb_textedit.h"
                 "${IMGUI_SOURCE_DIR}/imstb_truetype.h"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout.h"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout_internal.h"
)

set(includes
    "${CMAKE_CURRENT_SOURCE_DIR}"
    "${CMAKE_CURRENT_SOURCE_DIR}/backends"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/cpp"
)

target_link_libraries(imgui PRIVATE glfw)
target_include_directories(imgui PUBLIC ${includes} )
