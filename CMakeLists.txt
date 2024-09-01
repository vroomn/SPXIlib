project("SPXI")

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
	PRIVATE
		src/SPXI_lib.c
)