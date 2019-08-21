add_executable(${MBEDTLS_EXAMPLES_PREFIX_}dh_client dh_client.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}dh_client mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}dh_client PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}dh_genprime dh_genprime.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}dh_genprime mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}dh_genprime PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}dh_server dh_server.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}dh_server mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}dh_server PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ecdh_curve25519 ecdh_curve25519.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ecdh_curve25519 mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ecdh_curve25519 PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}ecdsa ecdsa.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}ecdsa mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}ecdsa PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}gen_key gen_key.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}gen_key mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}gen_key PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}key_app key_app.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}key_app mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}key_app PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}key_app_writer key_app_writer.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}key_app_writer mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}key_app_writer PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}mpi_demo mpi_demo.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}mpi_demo mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}mpi_demo PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_genkey rsa_genkey.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_genkey mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_genkey PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign rsa_sign.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify rsa_verify.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign_pss rsa_sign_pss.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign_pss mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign_pss PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify_pss rsa_verify_pss.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify_pss mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify_pss PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_encrypt rsa_encrypt.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_encrypt mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_encrypt PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}rsa_decrypt rsa_decrypt.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}rsa_decrypt mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}rsa_decrypt PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}pk_sign pk_sign.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}pk_sign mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}pk_sign PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}pk_verify pk_verify.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}pk_verify mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}pk_verify PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}pk_encrypt pk_encrypt.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}pk_encrypt mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}pk_encrypt PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

add_executable(${MBEDTLS_EXAMPLES_PREFIX_}pk_decrypt pk_decrypt.c)
target_link_libraries(${MBEDTLS_EXAMPLES_PREFIX_}pk_decrypt mbedtls)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}pk_decrypt PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Examples/pkey)

IF(MBEDTLS_ENABLE_INSTALL)
    install(TARGETS ${MBEDTLS_EXAMPLES_PREFIX_}dh_client
        ${MBEDTLS_EXAMPLES_PREFIX_}dh_genprime
        ${MBEDTLS_EXAMPLES_PREFIX_}dh_server
        ${MBEDTLS_EXAMPLES_PREFIX_}key_app
        ${MBEDTLS_EXAMPLES_PREFIX_}mpi_demo
        ${MBEDTLS_EXAMPLES_PREFIX_}rsa_genkey
        ${MBEDTLS_EXAMPLES_PREFIX_}rsa_sign
        ${MBEDTLS_EXAMPLES_PREFIX_}rsa_verify
        ${MBEDTLS_EXAMPLES_PREFIX_}rsa_encrypt
        ${MBEDTLS_EXAMPLES_PREFIX_}rsa_decrypt
        ${MBEDTLS_EXAMPLES_PREFIX_}pk_encrypt
        ${MBEDTLS_EXAMPLES_PREFIX_}pk_decrypt
        ${MBEDTLS_EXAMPLES_PREFIX_}pk_sign
        ${MBEDTLS_EXAMPLES_PREFIX_}pk_verify
        ${MBEDTLS_EXAMPLES_PREFIX_}gen_key
        DESTINATION "bin"
        PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
ENDIF(MBEDTLS_ENABLE_INSTALL)