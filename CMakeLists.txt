cmake_minimum_required(VERSION 2.8)

project (hiredis)

set(CMAKE_DEBUG_POSTFIX "d")

file(GLOB_RECURSE SOURCE_FILES *.h)

set(SOURCE_FILES ${SOURCE_FILES}
	async.c
	dict.c
	hiredis.c
	read.c
	net.c
	sds.c
)

add_library (hiredis ${SOURCE_FILES})

install(TARGETS hiredis
	EXPORT hiredis-config
	RUNTIME DESTINATION bin
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
	INCLUDES DESTINATION include/hiredis)
install(EXPORT hiredis-config
	DESTINATION cmake)
	
install(DIRECTORY .
	DESTINATION include/hiredis
	FILES_MATCHING PATTERN "*.h")
	
#install(DIRECTORY adapters
#	DESTINATION include/adapters
#	PATTERN "h")
	
#add_executable(hiredis-libuv examples/example-libuv.c)
#target_link_libraries(hiredis-libuv hiredis uv ws2_32.lib userenv.lib psapi.lib iphlpapi.lib)
#target_link_libraries(hiredis-libuv hiredis uv ws2_32.lib psapi.lib iphlpapi.lib userenv.lib)
#target_include_directories(hiredis-libuv 
#	PUBLIC .)
