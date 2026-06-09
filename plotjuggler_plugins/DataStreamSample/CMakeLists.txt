include_directories(../)

set(SRC datastream_sample.cpp)

add_library(DataStreamSample SHARED ${SRC} ${UI_SRC})

target_link_libraries(DataStreamSample PRIVATE Qt6::Widgets Qt6::Xml
                                               plotjuggler_base)

target_compile_definitions(DataStreamSample PRIVATE QT_PLUGIN)

install(TARGETS DataStreamSample DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
