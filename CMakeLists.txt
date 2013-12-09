cmake_minimum_required (VERSION 3.12)

project (nana-example)

set_property (GLOBAL PROPERTY USE_FOLDERS ON)

set (CMAKE_CXX_STANDARD 14)
set (CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Threads)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/nana)

### APP
set (APP_NAME "${PROJECT_NAME}-helloworld")

set (EXAMPLES_PATH "${PROJECT_SOURCE_DIR}/example")

include_directories (
    ${NANA_INCLUDE_DIR}
    ${NANA_BINARY_PATH}
    ${CMAKE_CURRENT_BINARY_DIR}
)
# target_include_directories(${APP_NAME} PUBLIC )

file (GLOB APP_SOURCE_FILES "${EXAMPLES_PATH}/*.cpp")
message(STATUS "APP_SOURCE_FILES: ${APP_SOURCE_FILES}" )

add_executable (${APP_NAME}
        ${APP_SOURCE_FILES}
        )

target_link_libraries (${APP_NAME}
        nana
        Threads::Threads
        X11
        rt
        Xft
        asound
        fontconfig
        Xcursor
        stdc++fs
        )

target_include_directories(${APP_NAME}
        PUBLIC
        )
