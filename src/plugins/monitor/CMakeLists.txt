CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
PROJECT(TDengine)

INCLUDE_DIRECTORIES(inc)
INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/client/inc)
INCLUDE_DIRECTORIES(${TD_COMMUNITY_DIR}/src/query/inc)
AUX_SOURCE_DIRECTORY(./src SRC)

ADD_LIBRARY(monitor ${SRC})

IF (TD_SOMODE_STATIC)
  TARGET_LINK_LIBRARIES(monitor taos_static)
ELSE ()
  TARGET_LINK_LIBRARIES(monitor taos)
ENDIF ()
