set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

find_package(Qt6AV QUIET)

if(NOT Qt6AV_FOUND)
  message(
    "Qt6AV not found. VideoPlayer plugin will not be built. Try installing it with 'sudo apt install libqtav-dev'"
  )
else()
  message("Qt6AV FOUND. Building VideoPlayer plugin")

  include_directories(../ ${QTAVWIDGETS_INCLUDE_DIRS})

  qt6_wrap_ui(UI_SRC video_dialog.ui)

  add_library(PublisherVideoViewer SHARED video_viewer.cpp video_dialog.cpp
                                          ${UI_SRC})

  target_link_libraries(
    PublisherVideoViewer PRIVATE Qt6::Widgets ${QTAVWIDGETS_LIBRARIES}
                                 plotjuggler_base)

  target_compile_definitions(PublisherVideoViewer PRIVATE QT_PLUGIN)
  install(TARGETS PublisherVideoViewer
          DESTINATION ${PJ_PLUGIN_INSTALL_DIRECTORY})
endif()
