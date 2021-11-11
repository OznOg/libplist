
add_executable(plist_cmp plist_cmp.c)
target_link_libraries(plist_cmp PRIVATE plist cnary)

add_executable(plist_test plist_test.c)
target_link_libraries(plist_test PRIVATE plist)

set(TEST_LIST empty.test
        small.test
        medium.test
        large.test
        huge.test
        bigarray.test
        dates.test
        timezone1.test
        timezone2.test
        signedunsigned1.test
        signedunsigned2.test
        signedunsigned3.test
        hex.test
        order.test
        recursion.test
        entities.test
        empty_keys.test
        amp.test
        invalid_tag.test
        cdata.test
        offsetsize.test
        refsize.test
        malformed_dict.test)

foreach(test ${TEST_LIST})
    add_test(NAME ${test} COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/${test})
    set_property(TEST ${test} PROPERTY ENVIRONMENT top_srcdir=${CMAKE_SOURCE_DIR} top_builddir=${CMAKE_BINARY_DIR})
endforeach()
