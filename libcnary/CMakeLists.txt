set(CMAKE_C_STANDARD 99)


add_library(cnary STATIC 
        node.c
        node_list.c)

target_include_directories(cnary PUBLIC include)

set_target_properties(cnary PROPERTIES
                                     VERSION 2.2.1
                                     SOVERSION 2
                                     DEBUG_POSTFIX D
                                     POSITION_INDEPENDENT_CODE ON)
