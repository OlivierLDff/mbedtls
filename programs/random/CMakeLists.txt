add_executable(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_havege gen_random_havege.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_havege mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_havege PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/random)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_ctr_drbg gen_random_ctr_drbg.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_ctr_drbg mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}gen_random_ctr_drbg PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/random)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}gen_entropy gen_entropy.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}gen_entropy mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}gen_entropy PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/random)

IF(MBEDTLS_ENABLE_INSTALL)
    install(TARGETS ${MBEDTLS_EXAMPLES_PREFIX_}gen_random_havege ${MBEDTLS_EXAMPLES_PREFIX_}gen_random_ctr_drbg ${MBEDTLS_EXAMPLES_PREFIX_}gen_entropy
        DESTINATION "bin"
        PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
ENDIF(MBEDTLS_ENABLE_INSTALL)