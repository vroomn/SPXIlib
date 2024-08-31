project("SPXI")

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
	PRIVATE
		src/SPXI_lib.c
)

#target_include_directories(${PROJECT_NAME}
#	PRIVATE
#		${CMAKE_CURRENT_SOURCE_DIR}/src
#	PUBLIC
#		$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
#		$<INSTALL_INTERFACE:${CMAKE_CURRENT_INSTALLDIR}>
#)