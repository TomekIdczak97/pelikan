# TODO(yao): include path hierarchy in lib name to avoid duplicates
# such as foo/memcache.c and bar/memcache.c
set(suite memcache)
set(test_name check_${suite})

set(source check_${suite}.c)

add_executable(${test_name} ${source})
target_link_libraries(${test_name} protocol_${suite})
target_link_libraries(${test_name} ccommon-static ${CHECK_LIBRARIES} pthread m)

add_dependencies(check ${test_name})
add_test(${test_name} ${test_name})
