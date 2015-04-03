cmake_minimum_required(VERSION 2.8.3)
project(prosilica_gige_sdk)
find_package(catkin REQUIRED )

# execute_process(
#   COMMAND mkdir -p ${PROJECT_SOURCE_DIR}/tgz)
# catkin_download_test_data(download_Prosilica_SDK
#   http://pr.willowgarage.com/downloads/Prosilica%20GigE%20SDK%201.20%20Linux.tgz
#   DESTINATION ${PROJECT_SOURCE_DIR}/tgz
#   )
# add_custom_command(
#   OUTPUT unpack_tgz
#   COMMAND tar zxvf ${PROJECT_SOURCE_DIR}/tgz/Prosilica%20GigE%20SDK%201.20%20Linux.tgz&& echo "HEYEYEYEYEYE"
#   DEPENDS download_Prosilica_SDK
#   )


#add_dependencies( unpack_tgz download_Prosilica_SDK.tgz )
# add_custom_target(downloads ALL DEPENDS download_Prosilica_SDK unpack_tgz)

catkin_package(
    DEPENDS
    CATKIN_DEPENDS
    INCLUDE_DIRS
    LIBRARIES
)

include_directories(include)
link_directories(${PROJECT_SOURCE_DIR}/lib)
link_libraries(PvAPI)
add_definitions(-D_LINUX -D_x86)
set(EXAMPLES build/Prosilica_GigE_SDK/examples)

# set_property(SOURCE ${EXAMPLES}/CLIpConfig/CLIpConfig.cpp APPEND PROPERTY OBJECT_DEPENDS download_Prosilica_SDK)
# set_property(SOURCE unit-tests.cpp APPEND PROPERTY OBJECT_DEPENDS testData.cpp)
# set_property(SOURCE unit-tests.cpp APPEND PROPERTY OBJECT_DEPENDS testData.cpp)
# set_property(SOURCE unit-tests.cpp APPEND PROPERTY OBJECT_DEPENDS testData.cpp)
# set_property(SOURCE unit-tests.cpp APPEND PROPERTY OBJECT_DEPENDS testData.cpp)

add_executable(CLIpConfig ${EXAMPLES}/CLIpConfig/CLIpConfig.cpp)
add_executable(Ping ${EXAMPLES}/Ping/Ping.cpp)
add_executable(ListCameras ${EXAMPLES}/ListCameras/ListCameras.cpp)
add_executable(ResetCamera ${EXAMPLES}/ResetCamera/ResetCamera.cpp)
add_executable(ListAttributes ${EXAMPLES}/ListAttributes/ListAttributes.cpp)

# add_custom_target(CLIpConfig ALL DEPENDS downloads)

# add_dependencies(CLIpConfig downloads)
# add_dependencies(Ping unpack_tgz)
# add_dependencies(ListCameras unpack_tgz)
# add_dependencies(ResetCamera unpack_tgz)
# add_dependencies(ListAttributes unpack_tgz)

