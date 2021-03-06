PROJECT(RGBDSensorToReactive)

# Use MRPT:
FIND_PACKAGE( MRPT REQUIRED slam gui hwdrivers maps graphslam opengl )

FIND_PACKAGE(OpenCV REQUIRED )
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})

find_path(OPENNI2_INCLUDE_DIR OpenNI.h
		  HINTS ${PC_OPENNI_INCLUDEDIR} ${PC_OPENNI_INCLUDE_DIRS} /usr/include/openni2 /usr/include/ni2
		  PATHS "$ENV{PROGRAMFILES}/OpenNI2/Include" "$ENV{PROGRAMW6432}/OpenNI2/Include" "$ENV{${ENV_OPNI2_INCLUDE}}" "$ENV{OPENNI2_INCLUDE}"
		  PATH_SUFFIXES openni ni
		  DOC "Path to the include directory containing OpenNI.h,etc.")
#add a hint so that it can find it without the pkg-config
find_library(OPENNI2_LIBRARY
			 NAMES OpenNI2
			 HINTS ${PC_OPENNI_LIBDIR} ${PC_OPENNI_LIBRARY_DIRS} /usr/lib
			 PATHS "$ENV{PROGRAMFILES}/OpenNI2/Redist" "$ENV{PROGRAMW6432}/OpenNI2/Redist" "$ENV{PROGRAMW6432}/OpenNI2" "$ENV{${ENV_OPNI2_LIB}}" "$ENV{OPENNI2_LIB}"
			 PATH_SUFFIXES lib lib64
			 DOC "The OpenNI2.lib file path")

#set(OPENNI2_INCLUDE_DIRS ${OPENNI2_INCLUDE_DIR})
#set(OPENNI2_LIBRARIES ${OPENNI2_LIBRARY})

#INCLUDE_DIRECTORIES($ENV{OPENNI2_INCLUDE})
#LINK_DIRECTORIES($ENV{OPENNI2_LIB})

INCLUDE_DIRECTORIES( ${MOOS_INCLUDE_DIRS}  )
LINK_DIRECTORIES( ${MOOS_LIBRARY_DIRS} )

INCLUDE_DIRECTORIES( ${OPENNI2_INCLUDE_DIR}  )
LINK_DIRECTORIES( ${OPENNI2_LIBRARY} )

# Add executable
ADD_EXECUTABLE( ${PROJECT_NAME}
	main.cpp
	CRGBD_App.cpp
	CRGBD_App.h
	)

	
#Message(Hola ${OpenCV_INCLUDE_DIRS})	
	
# Link the executable
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${MOOS_LIBRARIES} ${MRPT_LIBS}  
                                   ${OpenCV_LIBS} ${OPENNI2_LIBRARY})

