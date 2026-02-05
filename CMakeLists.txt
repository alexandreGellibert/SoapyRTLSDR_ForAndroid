cmake_minimum_required(VERSION 3.10)

project(SoapyRTLSDR LANGUAGES CXX)

# SoapyRTLSDR est un MODULE (plugin)
add_library(SoapyRTLSDR MODULE
        Registration.cpp
        Streaming.cpp
        Settings.cpp
)

# Includes
target_include_directories(SoapyRTLSDR PRIVATE
        ${CMAKE_SOURCE_DIR}/SoapySDR/include
        ${CMAKE_SOURCE_DIR}/rtl-sdr/include
)

# Link libraries
target_link_libraries(SoapyRTLSDR PRIVATE
        SoapySDR
        rtlsdr
        log
        android
        atomic
)

set_target_properties(SoapyRTLSDR PROPERTIES
        PREFIX "lib"
        SUFFIX ".so"
)
