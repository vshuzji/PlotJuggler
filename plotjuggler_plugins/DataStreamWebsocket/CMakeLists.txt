find_package(Qt6 REQUIRED COMPONENTS WebSockets)

if(NOT Qt6WebSockets_FOUND)
  message(
    STATUS
      "Can't find Qt6WebSockets in your system. Have you tried [sudo apt-get install libqt5websockets5-dev] ?"
  )
else()

  include_directories(../)

  qt6_wrap_ui(UI_SRC websocket_server.ui)

  set(SRC websocket_server.cpp)

  add_library(DataStreamWebSocket SHARED ${SRC} ${UI_SRC})

  target_link_libraries(DataStreamWebSocket
    PRIVATE
    Qt6::Widgets
    Qt6::WebSockets
    plotjuggler_base)

  target_compile_definitions(DataStreamWebSocket PRIVATE QT_PLUGIN)

  install(TARGETS DataStreamWebSocket
          DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})

endif()
