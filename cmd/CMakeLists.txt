cmake_minimum_required(VERSION 3.13)

project(mctp-cmd-rp1 C CXX ASM)

add_executable(${PROJECT_NAME}
    ${CMD_ROOT}/main.c
    ${CMD_ROOT}/commands.h
)
target_link_libraries(${PROJECT_NAME}
    rp1-smbus
    rp1-mctp
)
target_include_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${INCLUDE_ROOT}/smbus/smbus>
    $<BUILD_INTERFACE:${INCLUDE_ROOT}/mctp/mctp>
)
target_compile_options(${PROJECT_NAME} PRIVATE -Wall)