

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

set(C++HEADERS ${CMAKE_SOURCE_DIR}/include/plist/Array.h
        ${CMAKE_SOURCE_DIR}/include/plist/Boolean.h
        ${CMAKE_SOURCE_DIR}/include/plist/Data.h
        ${CMAKE_SOURCE_DIR}/include/plist/Date.h
        ${CMAKE_SOURCE_DIR}/include/plist/Dictionary.h
        ${CMAKE_SOURCE_DIR}/include/plist/Integer.h
        ${CMAKE_SOURCE_DIR}/include/plist/Key.h
        ${CMAKE_SOURCE_DIR}/include/plist/Node.h
        ${CMAKE_SOURCE_DIR}/include/plist/plist.h
        ${CMAKE_SOURCE_DIR}/include/plist/plist++.h
        ${CMAKE_SOURCE_DIR}/include/plist/Real.h
        ${CMAKE_SOURCE_DIR}/include/plist/String.h
        ${CMAKE_SOURCE_DIR}/include/plist/Structure.h
        ${CMAKE_SOURCE_DIR}/include/plist/Uid.h)

set_target_properties(plist PROPERTIES PUBLIC_HEADER "${C++HEADERS}")

set_target_properties(plist++  PROPERTIES VERSION 2.2.1 
                                          SOVERSION 2
                                          DEBUG_POSTFIX D)

target_link_libraries(plist++ PUBLIC plist)

install(TARGETS plist plist++
        EXPORT plistutil_export
        PUBLIC_HEADER
          DESTINATION include/plist)
