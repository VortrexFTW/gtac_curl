disable_rtti()

INCLUDE_DIRECTORIES("../curl_lib/include/curl")
LINK_DIRECTORIES("../curl_lib"/lib)

file(GLOB_RECURSE SOURCES *.cpp *.h)

if(MSVC)
	precompiled_header(pch)
endif()

new_library_shared(mod_curl "${SOURCES}" "")
if(WIN32)
target_link_libraries(mod_curl libcurl)
else()
target_link_libraries(mod_curl curl)
endif()
set_target_properties(mod_curl PROPERTIES FOLDER modules)