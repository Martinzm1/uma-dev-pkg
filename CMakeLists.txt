# +====================================================================+
# |          Open MObile Robot Architecture (MORA)                     |
# |                                                                    |
# |                 https://github.com/OpenMORA                        |
# |                                                                    |
# | Copyright individual authors (C) 2010-14  - See AUTHORS.txt        |
# | Project released under BSD License                                 |
# +====================================================================+

set(CMAKE_ALLOW_LOOSE_LOOP_CONSTRUCTS true)  # Simpler CMake syntax.
CMAKE_MINIMUM_REQUIRED(VERSION 2.8.11) # Minimum version required by MOOS v10 cfg files

PROJECT(uma_dev_pkg)

cmake_policy(SET CMP0003 NEW)  # Don't mix rel & abs lib paths
cmake_policy(SET CMP0005 NEW)  # Autoescape -D definitions

FIND_PACKAGE(MORA REQUIRED)  # Import MOOS vars, MORA CMake macros,etc.

MORA_COMMON_CMAKE() # Set common CMake options

SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${${PROJECT_NAME}_SOURCE_DIR}/cmakemodules")

# Add modules (dir names match modules' by default)
DEFINE_MORA_PROGRAM(CamControl_ImagingSource)
DEFINE_MORA_PROGRAM(SkypeComm_WindowsAPI)
DEFINE_MORA_PROGRAM(VirtualCam_Desktop)
DEFINE_MORA_PROGRAM(Arm_Kinova)
DEFINE_MORA_PROGRAM(MobileRobot_Segway)
DEFINE_MORA_PROGRAM(RGBDSensorToReactive)
DEFINE_MORA_PROGRAM(TEST_extRGBDSensor)
DEFINE_MORA_PROGRAM(pFaceDetector)
#DEFINE_MORA_PROGRAM(pSkeletonTracker)
#DEFINE_MORA_PROGRAM(pPersonDetector)
DEFINE_MORA_PROGRAM(pImageGrabber)
DEFINE_MORA_PROGRAM(pManPublisher)
DEFINE_MORA_PROGRAM(pFaceRecognizer)