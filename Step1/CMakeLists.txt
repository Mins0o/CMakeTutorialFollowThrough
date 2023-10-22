cmake_minimum_required(VERSION 3.10)

project(Tutorial LANGUAGES CXX VERSION 1.0)
# TODO 7: Set the project version number as 1.0 in the above project command


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# TODO 8: Use configure_file to configure and copy TutorialConfig.h.in to
#         TutorialConfig.h
option(FOO_ENABLE "Help message of FOO_ENABLE" ON)
option(FOO_DISABLE "Disabling the FOO_DISABLE" OFF)
set(BAR_STRING " ")
if(FOO_ENABLE)
    set(FOO_STRING "foo")
endif()
configure_file("TutorialConfig.h.in" "TutorialConfig.h")

# >>> output 
#   #define FOO_ENABLE
#   /* #undef FOO_DISABLE */
#   /* #undef NOONE_CARES */
#   #define FOO_STRING "foo"
#   #define BAR_STRING "foo"



add_executable(Tutorial tutorial.cxx)

# TODO 9: Use target_include_directories to include ${PROJECT_BINARY_DIR}
target_include_directories(Tutorial PUBLIC ${PROJECT_BINARY_DIR})
