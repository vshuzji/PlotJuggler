include_directories(../)

qt6_wrap_ui(UI_SRC lua_editor.ui)

add_library(ToolboxLuaEditor SHARED lua_editor.cpp lua_editor.h ${UI_SRC})

target_link_libraries(
  ToolboxLuaEditor PRIVATE Qt6::Widgets Qt6::Xml plotjuggler_base
                           plotjuggler_qwt QCodeEditor lua::lua)

target_compile_definitions(ToolboxLuaEditor PRIVATE QT_PLUGIN)

install(TARGETS ToolboxLuaEditor DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
