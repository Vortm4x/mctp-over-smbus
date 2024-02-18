cmake_minimum_required(VERSION 3.13)

project(mctp-over-smbus C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(PROJECT_ROOT "${CMAKE_CURRENT_LIST_DIR}")
set(INCLUDE_ROOT "${PROJECT_ROOT}/include")
set(LIB_ROOT "${PROJECT_ROOT}/lib")
set(CMD_ROOT "${PROJECT_ROOT}/cmd")


# SYSROOT_ENV BEGIN 
set(RASPBIAN_DIR "$ENV{HOME}/raspbian")
set(RASPBIAN_TARGET_ROOT "${RASPBIAN_DIR}/sshfs")
set(CMAKE_SYSROOT "${RASPBIAN_DIR}/cross-compile/chroots/rpi-bullseye-armhf")
set(RASPBIAN_INSTALL_PREFIX "${RASPBIAN_TARGET_ROOT}/home/pi")
# SYSROOT_ENV BEGIN


add_subdirectory("${LIB_ROOT}/smbus")
add_subdirectory("${LIB_ROOT}/mctp")

add_subdirectory("${CMD_ROOT}")

install(
    TARGETS mctp-cmd-rp1
    RUNTIME
    DESTINATION "${RASPBIAN_INSTALL_PREFIX}/mctp/"
)