disable_rtti()

INCLUDE_DIRECTORIES("../curl/include/curl")

file(GLOB_RECURSE SOURCES *.cpp *.h)

if(MSVC)
	precompiled_header(pch)
endif()

new_library_shared(gtac_curl "${SOURCES}" "")

# Link with Curl
target_link_libraries(gtac_curl CURL)

set_target_properties(gtac_curl PROPERTIES FOLDER modules)