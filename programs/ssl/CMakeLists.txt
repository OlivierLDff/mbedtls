set(THREADS_USE_PTHREADS_WIN32 true)
find_package(Threads)

set(libs
    mbedtls
)

set(targets
    ${MBEDTLS_EXAMPLES_PREFIX_}dtls_client
    ${MBEDTLS_EXAMPLES_PREFIX_}dtls_server
    ${MBEDTLS_EXAMPLES_PREFIX_}ssl_client1
    ${MBEDTLS_EXAMPLES_PREFIX_}ssl_client2
    ${MBEDTLS_EXAMPLES_PREFIX_}ssl_server
    ${MBEDTLS_EXAMPLES_PREFIX_}ssl_fork_server
    ${MBEDTLS_EXAMPLES_PREFIX_}ssl_mail_client
    ${MBEDTLS_EXAMPLES_PREFIX_}mini_client
)

if(USE_PKCS11_HELPER_LIBRARY)
    set(libs ${libs} pkcs11-helper)
endif(USE_PKCS11_HELPER_LIBRARY)

if(ENABLE_ZLIB_SUPPORT)
    set(libs ${libs} ${ZLIB_LIBRARIES})
endif(ENABLE_ZLIB_SUPPORT)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}dtls_client dtls_client.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}dtls_client ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}dtls_client PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}dtls_server dtls_server.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}dtls_server ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}dtls_server PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client1 ssl_client1.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client1 ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client1 PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client2 ssl_client2.c)
target_sources(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client2 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/query_config.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client2 ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_client2 PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server ssl_server.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server2 ssl_server2.c)
target_sources(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server2 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/query_config.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server2 ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_server2 PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_fork_server ssl_fork_server.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_fork_server ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_fork_server PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_mail_client ssl_mail_client.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_mail_client ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_mail_client PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}mini_client mini_client.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}mini_client ${libs})
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}mini_client PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)

if(THREADS_FOUND)
    add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ssl_pthread_server ssl_pthread_server.c)
    target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ssl_pthread_server ${libs} ${CMAKE_THREAD_LIBS_INIT})
    set(targets ${targets} ${MBEDTLS_EXAMPLES_PREFIX_}ssl_pthread_server)
    SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ssl_pthread_server PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/ssl)
endif(THREADS_FOUND)

IF(MBEDTLS_ENABLE_INSTALL)
    install(TARGETS ${targets}
            DESTINATION "bin"
            PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
ENDIF(MBEDTLS_ENABLE_INSTALL)