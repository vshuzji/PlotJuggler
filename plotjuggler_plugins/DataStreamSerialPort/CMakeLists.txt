find_package(Qt6 COMPONENTS SerialPort QUIET)

if(Qt6SerialPort_FOUND)
  message(STATUS "[Qt6SerialPort] found")

  qt6_wrap_ui(UI_SRC datastream_serialport.ui)

  set(SRC datastream_serialport.h datastream_serialport.cpp)

  add_library(DataStreamSerialPort SHARED ${SRC} ${UI_SRC})

  target_link_libraries(
    DataStreamSerialPort PRIVATE Qt6::Widgets Qt6::SerialPort plotjuggler_base)

  target_compile_definitions(DataStreamSerialPort PRIVATE QT_PLUGIN)

  install(TARGETS DataStreamSerialPort DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
else()
  message(WARNING "[Qt6SerialPort] not found. Skipping plugin DataStreamSerialPort.")
endif()
