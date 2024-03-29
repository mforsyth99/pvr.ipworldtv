project(pvr.ipworldtv)

cmake_minimum_required(VERSION 2.6)

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(kodiplatform REQUIRED)
find_package(platform REQUIRED)
find_package(ZLIB REQUIRED)

include_directories(${kodiplatform_INCLUDE_DIRS}
                    ${platform_INCLUDE_DIRS}
                    ${KODI_INCLUDE_DIR}
                    ${ZLIB_INCLUDE_DIRS}
                    ${PROJECT_SOURCE_DIR}/lib)

set(DEPLIBS ${platform_LIBRARIES}
            ${ZLIB_LIBRARIES})

message(STATUS "ZLIB_LIBRARIES: ${ZLIB_LIBRARIES}")

set(IPTV_SOURCES src/client.cpp
                 src/PVRIptvData.cpp)

build_addon(pvr.ipworldtv IPTV DEPLIBS)

include(CPack)
