cmake_minimum_required(VERSION 3.4.1)


INCLUDE_DIRECTORIES(
    ./includes
)

AUX_SOURCE_DIRECTORY(. DIR_SRCS)
AUX_SOURCE_DIRECTORY(./art ART_DIR)
AUX_SOURCE_DIRECTORY(./dalvik DALVIK_DIR)

ADD_LIBRARY(andfix SHARED
            ${DIR_SRCS} ${ART_DIR} ${DALVIK_DIR})

find_library( # Sets the name of the path variable.
              # 设置依赖库的名字，下面链接库的时候会用到
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.

              # 查找log依赖库
              # {sdk-path}/ndk-bundle/sysroot/usr/include/android/log.h
              log )

target_link_libraries(andfix
                      android
                      log)
