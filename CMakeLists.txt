if (NOT (WIN32 OR UNIX))
	return()
endif()

project(obs-shaderfilter)

if(WIN32)
	set(MODULE_DESCRIPTION "OBS HLSL shader module")
	set(obs-shaderfilter_PLATFORM_SOURCES
		${CMAKE_CURRENT_SOURCE_DIR}/src/obs-shaderfilter.c
	)
	add_library(obs-shaderfilter MODULE
		${obs-shaderfilter_PLATFORM_SOURCES}
	)
elseif(UNIX)
	set(obs-shaderfilter_SOURCES
		${CMAKE_CURRENT_SOURCE_DIR}/src/obs-shaderfilter.c
	)
	add_library(obs-shaderfilter MODULE
		${obs-shaderfilter_SOURCES}
	)
endif()

target_link_libraries(obs-shaderfilter
	libobs
)

install_obs_plugin_with_data(obs-shaderfilter data)

