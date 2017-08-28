project(image-source)

if(MSVC)
	set(image-source_PLATFORM_DEPS
		w32-pthreads)
endif()

#add multiple-image-source
set(image-source_HEADERS
	multiple-image-source.h)

set(image-source_SOURCES
	image-source.c
	color-source.c
	obs-slideshow.c
	multiple-image-source.c
	pen-source.c)

add_library(image-source MODULE
	${image-source_HEADERS}
	${image-source_SOURCES})
target_link_libraries(image-source
	libobs
	${image-source_PLATFORM_DEPS})

install_obs_plugin_with_data(image-source data)
