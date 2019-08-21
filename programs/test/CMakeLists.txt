set(libs
    mbedtls
)

if(USE_PKCS11_HELPER_LIBRARY)
    set(libs ${libs} pkcs11-helper)
endif(USE_PKCS11_HELPER_LIBRARY)

if(ENABLE_ZLIB_SUPPORT)
    set(libs ${libs} ${ZLIB_LIBRARIES})
endif(ENABLE_ZLIB_SUPPORT)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}selftest selftest.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}selftest ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}selftest PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}benchmark benchmark.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}benchmark ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}benchmark PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)

if(TEST_CPP)
    add_executable(${MBEDTLS_EXAMPLES_PREFIX_}cpp_dummy_build cpp_dummy_build.cpp)
    target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}cpp_dummy_build ${libs})
    SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}cpp_dummy_build PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)
endif()

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}udp_proxy udp_proxy.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}udp_proxy ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}udp_proxy PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}zeroize zeroize.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}zeroize ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}zeroize PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}query_compile_time_config query_compile_time_config.c)
target_sources(${MBEDTLS_EXAMPLES_PREFIX_}query_compile_time_config PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../ssl/query_config.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}query_compile_time_config ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}query_compile_time_config PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/test)

IF(MBEDTLS_ENABLE_INSTALL)
install(TARGETS ${MBEDTLS_EXAMPLES_PREFIX_}selftest ${MBEDTLS_EXAMPLES_PREFIX_}benchmark ${MBEDTLS_EXAMPLES_PREFIX_}udp_proxy ${MBEDTLS_EXAMPLES_PREFIX_}query_compile_time_config
        DESTINATION "bin"
        PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
ENDIF(MBEDTLS_ENABLE_INSTALL)
