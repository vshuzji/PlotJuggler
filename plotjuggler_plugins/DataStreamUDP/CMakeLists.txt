include_directories(../)

qt6_wrap_ui(UI_SRC udp_server.ui)

set(SRC udp_server.cpp)

add_library(DataStreamUDP SHARED ${SRC} ${UI_SRC})

target_link_libraries(DataStreamUDP PRIVATE Qt6::Widgets Qt6::Network
                                            plotjuggler_base)

target_compile_definitions(DataStreamUDP PRIVATE QT_PLUGIN)

install(TARGETS DataStreamUDP DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
