cmake_minimum_required(VERSION 3.13)

project(smbus-rp1 C CXX ASM)

set(LIB_DIR "smbus")

add_library(${PROJECT_NAME}
    ${LIB_ROOT}/${LIB_DIR}/smbus.c
    ${LIB_ROOT}/${LIB_DIR}/smbus_pec.c
)
target_link_libraries(${PROJECT_NAME}
    i2c
)
target_include_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${INCLUDE_ROOT}/${LIB_DIR}>
    $<INSTALL_INTERFACE:${INCLUDE_ROOT}/${LIB_DIR}/${LIB_DIR}>
)
target_compile_options(${PROJECT_NAME} PRIVATE -Wall)