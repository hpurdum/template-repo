
###########################################
# CMAKELISTS : TEMPLATE PROJECT           #
###########################################

# SET PROJECT VARIABLES
cmake_minimum_required(VERSION 3.26.0)
project(template VERSION 0.1)
set(CMAKE_CXX_STANDARD_REQUIRED 11)
set(CMAKE_CXX_FLAGS "-O2 -g -Wall -Werror")

# SET PROJECT SRC/INC FILES
set(template_src
    ...)
set(template_test_src
    ...)
set(template_inc
    ...)
set(template_test_inc
    ...)

# DEFINE PROJECT OPTIONS
option(TESTS "Build Tests" OFF)

# DEFINE PROJECT LIBRARIES (OPTIONAL)


# DEFINE EXECUTABLES
add_executable(template.o main/main.cpp ${template_src})
if(TESTS)
    enable_testing()
    add_executable(tests ext/googletest/googletest/src/gtest_main.cc ${template_test_src})
endif()

# DEFINE INCLUDE DIRECTORIES
target_include_directories(template.o
    PRIVATE
    ${template_inc})
if(TESTS)
    target_include_directories(tests
        PRIVATE
        ${template_test_inc})
endif()

# DEFINE SUBDIRECTORIES
if(TESTS)
    add_subdirectory(ext/googletest googletest)
endif()

# LINK LIBRARIES
if(TESTS)
    target_link_libraries(tests gtest)
endif(TESTS)

# INSTALL LIBRARIES (OPTIONAL)


# INSTALL BINARIES (OPTIONAL)


# BUILD MESSAGES (OPTIONAL)
# message("")
