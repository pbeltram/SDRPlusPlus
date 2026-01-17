cmake_minimum_required(VERSION 3.13)
project(papi_sdr_source)

file(GLOB SRC "src/*.cpp")

add_library(papi_sdr_source SHARED ${SRC})
target_link_libraries(papi_sdr_source PRIVATE sdrpp_core)
set_target_properties(papi_sdr_source PROPERTIES PREFIX "")

target_include_directories(papi_sdr_source PRIVATE "src/")

if (MSVC)
    target_compile_options(papi_sdr_source PRIVATE /O2 /Ob2 /std:c++17 /EHsc)
elseif (CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    target_compile_options(papi_sdr_source PRIVATE $<$<CONFIG:Release>:${MY_RELEASE_FLAGS}> $<$<CONFIG:Debug>:${MY_DEBUG_FLAGS}> -std=c++17 -Wno-unused-command-line-argument -undefined dynamic_lookup)
else ()
    target_compile_options(papi_sdr_source PRIVATE $<$<CONFIG:Release>:${MY_RELEASE_FLAGS}> $<$<CONFIG:Debug>:${MY_DEBUG_FLAGS}> -std=c++17)
endif ()

if (MSVC)
    # Lib path
    target_link_directories(papi_sdr_source PRIVATE "C:/Program Files/PapiSDR/lib/")
    target_include_directories(papi_sdr_source PRIVATE "C:/Program Files/PapiSDR/include/")

    target_link_libraries(papi_sdr_source PRIVATE libiio)
    target_link_libraries(papi_sdr_source PRIVATE libad9361)
else (MSVC)
    find_package(PkgConfig)

    pkg_check_modules(LIBIIO REQUIRED libiio)
    pkg_check_modules(LIBAD9361 REQUIRED libad9361)

    target_include_directories(papi_sdr_source PRIVATE ${LIBIIO_INCLUDE_DIRS})
    target_link_directories(papi_sdr_source PRIVATE ${LIBIIO_LIBRARY_DIRS})
    target_link_libraries(papi_sdr_source PRIVATE ${LIBIIO_LIBRARIES})

    target_include_directories(papi_sdr_source PRIVATE ${LIBAD9361_INCLUDE_DIRS})
    target_link_directories(papi_sdr_source PRIVATE ${LIBAD9361_LIBRARY_DIRS})
    target_link_libraries(papi_sdr_source PRIVATE ${LIBAD9361_LIBRARIES})
endif ()

# Install directives
install(TARGETS papi_sdr_source DESTINATION lib/sdrpp/plugins)
