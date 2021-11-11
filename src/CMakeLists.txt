

include_directories(${CMAKE_SOURCE_DIR}/libcnary/include)
include_directories(${CMAKE_SOURCE_DIR}/include)
include_directories(${CMAKE_SOURCE_DIR}/)
include_directories(${PROJECT_SOURCE_DIR})

find_package(Threads REQUIRED)


add_library(plist SHARED
        base64.c
        bplist.c
        bytearray.c
        hashtable.c
        plist.c
        ptrarray.c
        time64.c
        xplist.c)

target_include_directories(plist PRIVATE .)

set_target_properties(plist PROPERTIES PUBLIC_HEADER ${CMAKE_SOURCE_DIR}/include/plist/plist.h)

target_link_libraries(plist PRIVATE cnary
                            PUBLIC Threads::Threads $<$<NOT:$<BOOL:${WIN32}>>:m>)

set_target_properties(plist PROPERTIES VERSION 2.2.1
                                       SOVERSION 2
                                       DEBUG_POSTFIX D)
add_library(plist++ SHARED
        Array.cpp
        Boolean.cpp
        Data.cpp
        Date.cpp
        Dictionary.cpp
        Integer.cpp
        Key.cpp
        Node.cpp
        Real.cpp
        String.cpp
        Structure.cpp
        Uid.cpp)

set_target_properties(plist++  PROPERTIES VERSION 2.2.1 
                                          SOVERSION 2
                                          DEBUG_POSTFIX D)

target_link_libraries(plist++ PUBLIC plist)

