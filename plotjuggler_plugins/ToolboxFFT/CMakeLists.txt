include_directories(../)

add_subdirectory(3rdparty/KissFFT)

qt6_wrap_ui(UI_SRC toolbox_FFT.ui)

add_library(ToolboxFFT SHARED toolbox_FFT.cpp toolbox_FFT.h ${UI_SRC})

target_include_directories(ToolboxFFT PRIVATE 3rdparty)

find_package(Qt6 CONFIG REQUIRED COMPONENTS OpenGLWidgets)
target_link_libraries(ToolboxFFT PRIVATE
                                         Qt6::Core
                                         Qt6::Widgets
                                         Qt6::OpenGL
                                         Qt6::OpenGLWidgets
                                         Qt6::Xml
                                         kissfft
                                         plotjuggler_base
                                         plotjuggler_qwt)

target_compile_definitions(ToolboxFFT PRIVATE QT_PLUGIN)

install(TARGETS ToolboxFFT DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
