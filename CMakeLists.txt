PROJECT ( QVideoWriter )

CMAKE_MINIMUM_REQUIRED (VERSION 3.0)

SET( CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules/")

FIND_PACKAGE (Qt5Widgets REQUIRED)
FIND_PACKAGE (FFmpeg REQUIRED)
ADD_DEFINITIONS (${QT_DEFINITIONS})
ADD_DEFINITIONS (${FFMPEG_DEFINITIONS})

INCLUDE_DIRECTORIES (${QT_INCLUDE_DIR})
INCLUDE_DIRECTORIES (${FFMPEG_INCLUDE_DIRS})
INCLUDE_DIRECTORIES (${CMAKE_CURRENT_BINARY_DIR})
INCLUDE_DIRECTORIES (${CMAKE_CURRENT_SOURCE_DIR})
INCLUDE_DIRECTORIES (${CMAKE_CURRENT_SOURCE_DIR}/include)

SET ( QTFFMPEG_HDR
	QVideoWriter.h
)
SET ( QTFFMPEG_SRC
	src/QVideoWriter.cpp
)

ADD_LIBRARY ( qvideowriter STATIC ${QTFFMPEG_SRC} )

TARGET_LINK_LIBRARIES ( qvideowriter
	${Qt5Widgets_LIBRARIES}
	${Qt5Core_LIBRARIES}
	${QT_LIBRARIES}
	${FFMPEG_LIBRARIES}
	${SWSCALE_LIBRARIES}
)

