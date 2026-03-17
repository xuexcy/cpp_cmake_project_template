add_library(core)
target_sources(core PUBLIC
  FILE_SET CXX_MODULES
  FILES core/core.ixx core/base.cppm core/utils.cppm)

add_library(data)
target_sources(data PUBLIC
  FILE_SET CXX_MODULES
  FILES data/data.ixx data/user.cppm)
target_link_libraries(data core)

add_library(net)
target_sources(net PUBLIC
  FILE_SET CXX_MODULES
  FILES net/net.ixx net/client.cppm)

target_link_libraries(net core data)

add_library(shape)
target_sources(shape
  PUBLIC
    FILE_SET CXX_MODULES
    FILES shape/shape.cppm shape/point.cppm shape/rectangle.cppm
  PRIVATE
    shape/rectangle.cpp)
set_property(SOURCE shape/rectangle.cppm PROPERTY CXX_MODULE_NAME "shape:rectangle")
set_property(SOURCE shape/rectangle.cppm PROPERTY CXX_MODULE_IS_PARTITION ON)
set_property(SOURCE shape/point.cppm PROPERTY CXX_MODULE_NAME "shape:point")
set_property(SOURCE shape/point.cppm PROPERTY CXX_MODULE_IS_PARTITION ON)

add_library(hello_world)
target_sources(hello_world PUBLIC
  FILE_SET CXX_MODULES
  FILES hello_world.cppm)

add_executable(cpp23_module_main main.cc)
target_link_libraries(cpp23_module_main core data net shape hello_world)
