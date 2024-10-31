cmake_minimum_required(VERSION 3.4.1)

add_library(bzyuvlib SHARED native-lib.cpp bz_time.cpp BZLogUtil.cpp )

find_library(log-lib log)
find_library(jnigraphics-lib jnigraphics)

add_library(yuv-lib STATIC IMPORTED)
set_target_properties(yuv-lib PROPERTIES IMPORTED_LOCATION ${Project_SOURCE_DIR}/lib/${ANDROID_ABI}/libyuv_static.a)

include_directories(./ ./include/ ./include/libyuv/)

target_link_libraries(bzyuvlib yuv-lib ${log-lib} ${jnigraphics-lib})