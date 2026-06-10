include_directories(../)

qt6_wrap_ui(UI_SRC quaternion_to_rpy.ui)

add_library(ToolboxQuaternion SHARED toolbox_quaternion.cpp
                                     quaternion_to_rpy.cpp ${UI_SRC})

find_package(Qt6 CONFIG REQUIRED COMPONENTS OpenGLWidgets)

target_link_libraries(
  ToolboxQuaternion PRIVATE PRIVATE
  Qt6::Core
  Qt6::Widgets
  Qt6::OpenGL
  Qt6::OpenGLWidgets
  Qt6::Xml
  plotjuggler_base
  plotjuggler_qwt)

target_compile_definitions(ToolboxQuaternion PRIVATE QT_PLUGIN)

install(TARGETS ToolboxQuaternion DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
