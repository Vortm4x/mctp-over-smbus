cmake_minimum_required(VERSION 3.13)

project(mctp-rp1 C CXX ASM)

set(LIB_DIR "mctp")

add_library(${PROJECT_NAME}
    ${LIB_ROOT}/${LIB_DIR}/mctp.c
)
target_link_libraries(${PROJECT_NAME}
    smbus-rp1
)
target_include_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${INCLUDE_ROOT}/smbus/smbus>
    
    $<BUILD_INTERFACE:${INCLUDE_ROOT}/${LIB_DIR}>
    $<INSTALL_INTERFACE:${INCLUDE_ROOT}/${LIB_DIR}/${LIB_DIR}>
)
target_compile_options(${PROJECT_NAME} PRIVATE -Wall)