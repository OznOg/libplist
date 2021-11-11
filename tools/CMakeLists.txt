
set(PACKAGE_BUGREPORT "\"https://github.com/libimobiledevice/libplist/issues\"")
set(PACKAGE_URL \"https://libimobiledevice.org\")
set(PACKAGE_VERSION \"${PROJECT_VERSION}\")

add_executable(plistutil plistutil.c)

target_link_libraries(plistutil PRIVATE plist)
target_compile_definitions(plistutil PRIVATE PACKAGE_URL=${PACKAGE_URL}
                                             PACKAGE_BUGREPORT=${PACKAGE_BUGREPORT}
                                             PACKAGE_VERSION=${PACKAGE_VERSION})
