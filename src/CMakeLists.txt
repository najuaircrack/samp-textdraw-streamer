if (WIN32)
    cmake_minimum_required(VERSION 3.12)
else()
    cmake_minimum_required(VERSION 3.10.2)
endif()

project(textdraw-streamer VERSION 1.0)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(AMXConfig)
include(AddSAMPPlugin)

add_samp_plugin(textdraw-streamer
    amxplugin.cpp
    compilation_date.hpp
    main.cpp
    natives.hpp
    natives_data.cpp
    natives_global.cpp
    natives_player.cpp
    natives_plugin.cpp
    plugin.h
    plugin_version.hpp
    plugincommon.h
    sampgdk.cpp
    sampgdk.hpp
    service.cpp
    service.hpp
    slot_manager.cpp
    slot_manager.hpp
    textdraw_data.cpp
    textdraw_data.hpp
    textdraw-streamer.def
)

target_include_directories(textdraw-streamer PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/amx
    ${CMAKE_CURRENT_SOURCE_DIR}/fmt
)

target_compile_definitions(textdraw-streamer PRIVATE
    SAMPGDK_AMALGAMATION
    FMT_HEADER_ONLY
)
