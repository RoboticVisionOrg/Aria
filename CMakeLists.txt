cmake_minimum_required(VERSION 2.8.3)
project(rv_libaria)

set(CMAKE_BUILD_TYPE Release)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-format -Wno-format-security")

find_package(catkin REQUIRED)


###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if your package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
  LIBRARIES Aria ArNetworking
)

###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
  include
  ArNetworking/include
)

set(ARIA_SRC
  src/ArAction.cpp
  src/ArActionAvoidFront.cpp
  src/ArActionAvoidSide.cpp
  src/ArActionBumpers.cpp
  src/ArActionColorFollow.cpp
  src/ArActionConstantVelocity.cpp
  src/ArActionDeceleratingLimiter.cpp
  src/ArActionDesired.cpp
  src/ArActionDriveDistance.cpp
  src/ArActionGoto.cpp
  src/ArActionGotoStraight.cpp
  src/ArActionGroup.cpp
  src/ArActionGroups.cpp
  src/ArActionInput.cpp
  src/ArActionIRs.cpp
  src/ArActionJoydrive.cpp
  src/ArActionKeydrive.cpp
  src/ArActionLimiterBackwards.cpp
  src/ArActionLimiterForwards.cpp
  src/ArActionLimiterRot.cpp
  src/ArActionLimiterTableSensor.cpp
  src/ArActionMovementParameters.cpp
  src/ArActionMovementParametersDebugging.cpp
  src/ArActionRatioInput.cpp
  src/ArActionRobotJoydrive.cpp
  src/ArActionStallRecover.cpp
  src/ArActionStop.cpp
  src/ArActionTriangleDriveTo.cpp
  src/ArActionTurn.cpp
  src/ArACTS.cpp
  src/ArAMPTU.cpp
  src/ArAnalogGyro.cpp
  src/ArArg.cpp
  src/ArArgumentBuilder.cpp
  src/ArArgumentParser.cpp
  src/ArASyncTask.cpp
  src/ArBasePacket.cpp
  src/ArBatteryConnector.cpp
  src/ArBatteryMTX.cpp
  src/ArBumpers.cpp
  src/ArCameraCommands.cpp
  src/ArCameraCollection.cpp
  src/ArCondition_LIN.cpp
  src/ArConfig.cpp
  src/ArConfigArg.cpp
  src/ArConfigGroup.cpp
  src/ArDataLogger.cpp
  src/ArDeviceConnection.cpp
  src/ArDPPTU.cpp
  src/ArFileDeviceConnection.cpp
  src/ArFileParser.cpp
  src/ArForbiddenRangeDevice.cpp
  src/ArFunctorASyncTask.cpp
  src/ArGPS.cpp
  src/ArGPSConnector.cpp
  src/ArGPSCoords.cpp
  src/ArGripper.cpp
  src/ArInterpolation.cpp
  src/ArIrrfDevice.cpp
  src/ArIRs.cpp
  src/ArJoyHandler.cpp
  src/ArKeyHandler.cpp
  src/ArLaser.cpp
  src/ArLaserConnector.cpp
  src/ArLaserFilter.cpp
  src/ArLaserLogger.cpp
  src/ArLaserReflectorDevice.cpp
  src/ArLCDConnector.cpp
  src/ArLCDMTX.cpp
  src/ArLineFinder.cpp
  src/ArLMS1XX.cpp
  src/ArLMS2xx.cpp
  src/ArLMS2xxPacket.cpp
  src/ArLMS2xxPacketReceiver.cpp
  src/ArLog.cpp
  src/ArLogFileConnection.cpp
  src/ArMap.cpp
  src/ArMapComponents.cpp
  src/ArMapInterface.cpp
  src/ArMapObject.cpp
  src/ArMapUtils.cpp
  src/ArMD5Calculator.cpp
  src/ArMode.cpp
  src/ArModes.cpp
  src/ArModule.cpp
  src/ArModuleLoader.cpp
  src/ArMutex.cpp
  src/ArMutex_LIN.cpp
  src/ArNetServer.cpp
  src/ArNMEAParser.cpp
  src/ArNovatelGPS.cpp
  src/ArP2Arm.cpp
  src/ArPriorityResolver.cpp
  src/ArPTZ.cpp
  src/ArPTZConnector.cpp
  src/ArRangeBuffer.cpp
  src/ArRangeDevice.cpp
  src/ArRangeDeviceThreaded.cpp
  src/ArRatioInputKeydrive.cpp
  src/ArRatioInputJoydrive.cpp
  src/ArRatioInputRobotJoydrive.cpp
  src/ArRecurrentTask.cpp
  src/ArRobot.cpp
  src/ArRobotBatteryPacketReader.cpp
  src/ArRobotConfig.cpp
  src/ArRobotConfigPacketReader.cpp
  src/ArRobotConnector.cpp
  src/ArRobotJoyHandler.cpp
  src/ArRobotPacket.cpp
  src/ArRobotPacketReceiver.cpp
  src/ArRobotPacketReaderThread.cpp
  src/ArRobotPacketSender.cpp
  src/ArRobotParams.cpp
  src/ArRobotTypes.cpp
  src/ArRVisionPTZ.cpp
  src/ArS3Series.cpp
  src/ArSZSeries.cpp
  src/ArSick.cpp
  src/ArSimpleConnector.cpp
  src/ArSimulatedLaser.cpp
  src/ArSocket.cpp
  src/ArSonarConnector.cpp
  src/ArSonarDevice.cpp
  src/ArSonarMTX.cpp
  src/ArSensorReading.cpp
  src/ArSonyPTZ.cpp
  src/ArSoundsQueue.cpp
  src/ArSoundPlayer.cpp
  src/ArStringInfoGroup.cpp
  src/ArSyncLoop.cpp
  src/ArSyncTask.cpp
  src/ArSystemStatus.cpp
  src/ArSonarAutoDisabler.cpp
  src/ArSpeech.cpp
  src/ArTCM2.cpp
  src/ArTCMCompassDirect.cpp
  src/ArTCMCompassRobot.cpp
  src/ArTcpConnection.cpp
  src/ArThread.cpp
  src/ArThread_LIN.cpp
  src/ArTransform.cpp
  src/ArTrimbleGPS.cpp
  src/ArUrg.cpp
  src/ArUrg_2_0.cpp
  src/ArVCC4.cpp
  src/Aria.cpp
  src/ariaUtil.cpp
  src/md5.cpp
  src/ArSocket_LIN.cpp
  src/ArJoyHandler_LIN.cpp
  src/ArSerialConnection_LIN.cpp
  src/ArSignalHandler_LIN.cpp
  src/ArVersalogicIO.cpp
  src/ArMTXIO.cpp
)


set(AR_NETWORKING_SRC
  ArNetworking/src/ArCentralForwarder.cpp
  ArNetworking/src/ArCentralManager.cpp
  ArNetworking/src/ArClientArgUtils.cpp
  ArNetworking/src/ArClientBase.cpp
  ArNetworking/src/ArClientData.cpp
  ArNetworking/src/ArClientFileUtils.cpp
  ArNetworking/src/ArClientHandlerConfig.cpp
  ArNetworking/src/ArClientSimpleConnector.cpp
  ArNetworking/src/ArClientSwitchManager.cpp
  ArNetworking/src/ArHybridForwarderVideo.cpp
  ArNetworking/src/ArMapChanger.cpp
  ArNetworking/src/ArNetPacket.cpp
  ArNetworking/src/ArNetPacketReceiverTcp.cpp
  ArNetworking/src/ArNetPacketReceiverUdp.cpp
  ArNetworking/src/ArNetPacketSenderTcp.cpp
  ArNetworking/src/ArServerBase.cpp
  ArNetworking/src/ArServerClient.cpp
  ArNetworking/src/ArServerData.cpp
  ArNetworking/src/ArServerFileUtils.cpp
  ArNetworking/src/ArServerHandlerCameraCollection.cpp
  ArNetworking/src/ArServerHandlerCamera.cpp
  ArNetworking/src/ArServerHandlerCommands.cpp
  ArNetworking/src/ArServerHandlerCommMonitor.cpp
  ArNetworking/src/ArServerHandlerConfig.cpp
  ArNetworking/src/ArServerHandlerMap.cpp
  ArNetworking/src/ArServerHandlerMapping.cpp
  ArNetworking/src/ArServerHandlerPopup.cpp
  ArNetworking/src/ArServerInfoDrawings.cpp
  ArNetworking/src/ArServerInfoRobot.cpp
  ArNetworking/src/ArServerInfoSensor.cpp
  ArNetworking/src/ArServerInfoStrings.cpp
  ArNetworking/src/ArServerMode.cpp
  ArNetworking/src/ArServerModeDrive.cpp
  ArNetworking/src/ArServerModeIdle.cpp
  ArNetworking/src/ArServerModeRatioDrive.cpp
  ArNetworking/src/ArServerModeStop.cpp
  ArNetworking/src/ArServerModeWander.cpp
  ArNetworking/src/ArServerSimpleCommands.cpp
  ArNetworking/src/ArServerSimpleOpener.cpp
  ArNetworking/src/ArServerUserInfo.cpp
  ArNetworking/src/ArTempDirectoryHelper.cpp
  ArNetworking/src/md5.cpp
)

add_library(Aria SHARED ${ARIA_SRC})
add_library(ArNetworking SHARED ${AR_NETWORKING_SRC})

#############
## Install ##
#############

install(TARGETS Aria ArNetworking
   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include/Aria/
  DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}/Aria
  FILES_MATCHING PATTERN "*.h" PATTERN "*.hpp"
)

install(DIRECTORY ArNetworking/include/
  DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}/ArNetworking
  FILES_MATCHING PATTERN "*.h" PATTERN "*.hpp"
)