# ┌──────────────────────────────────────────────────────────────────┐
# │                       CMAKE PROPERTIES                           │
# └──────────────────────────────────────────────────────────────────┘

cmake_minimum_required(VERSION 3.11)

# ┌──────────────────────────────────────────────────────────────────┐
# │                       PROJECT SETTINGS                           │
# └──────────────────────────────────────────────────────────────────┘

# General
SET( MBEDTLS_PROJECT "mbedtls" CACHE STRING "Project Name")
SET( MBEDTLS_TARGET "${MBEDTLS_PROJECT}" CACHE STRING "mbedtls library name" )
SET( MBEDTLS_VERSION "2.18.1" CACHE STRING "mbedtls current version, this is only decorative and will not configure any files" FORCE )
SET( MBEDTLS_BUILD_SHARED OFF CACHE BOOL "Build as a shared library (ON) or as static (OFF)" )
SET( MBEDTLS_FOLDER_PREFIX ${MBEDTLS_TARGET} CACHE STRING "Prefix folder for all mbedtls generated targets in generated project (only decorative)" )
SET( MBEDTLS_UNSAFE_BUILD OFF CACHE BOOL "Allow unsafe builds. These builds ARE NOT SECURE" )
SET( MBEDTLS_LINK_WITH_PTHREAD OFF CACHE BOOL "Explicitly link mbed crypto library to pthread." )

# Tests
SET( MBEDTLS_ENABLE_TESTS OFF CACHE BOOL "Create or not a target for test (compatible with CTests)" )
SET( MBEDTLS_TESTS_PREFIX ${MBEDTLS_TARGET} CACHE STRING "Prefix for all mbedtls tests" )
IF(NOT ${MBEDTLS_TESTS_PREFIX} STREQUAL "")
    SET( MBEDTLS_TESTS_PREFIX_ "${MBEDTLS_TESTS_PREFIX}_" )
ELSE(NOT ${MBEDTLS_TESTS_PREFIX} STREQUAL "")
    SET( MBEDTLS_TESTS_PREFIX_ "" )
ENDIF(NOT ${MBEDTLS_TESTS_PREFIX} STREQUAL "")

# Examples
SET( MBEDTLS_ENABLE_EXAMPLES OFF CACHE BOOL "Create or not a target for examples" )
SET( MBEDTLS_EXAMPLES_PREFIX ${MBEDTLS_TARGET} CACHE STRING "Prefix for all mbedtls tests" )
IF(NOT ${MBEDTLS_EXAMPLES_PREFIX} STREQUAL "")
    SET( MBEDTLS_EXAMPLES_PREFIX_ "${MBEDTLS_EXAMPLES_PREFIX}_" )
ELSE(NOT ${MBEDTLS_EXAMPLES_PREFIX} STREQUAL "")
    SET( MBEDTLS_EXAMPLES_PREFIX_ "" )
ENDIF(NOT ${MBEDTLS_EXAMPLES_PREFIX} STREQUAL "")

# Install
SET( MBEDTLS_ENABLE_INSTALL OFF CACHE BOOL "Create or not a target for install" )
SET( MBEDTLS_INSTALL_PREFIX ${MBEDTLS_TARGET} CACHE STRING "Prefix for all mbedtls headers in the install folder" )

if(TEST_CPP)
    project(${MBEDTLS_PROJECT} LANGUAGES C CXX VERSION ${MBEDTLS_VERSION})
else()
    project(${MBEDTLS_PROJECT} LANGUAGES C VERSION ${MBEDTLS_VERSION})
endif()
SET_PROPERTY(GLOBAL PROPERTY USE_FOLDERS ON)

option(USE_PKCS11_HELPER_LIBRARY "Build mbed TLS with the pkcs11-helper library." OFF)
option(ENABLE_ZLIB_SUPPORT "Build mbed TLS with zlib library." OFF)

option(ENABLE_PROGRAMS "Build mbed TLS programs." ${MBEDTLS_ENABLE_EXAMPLES})

option(UNSAFE_BUILD "Allow unsafe builds. These builds ARE NOT SECURE." ${MBEDTLS_UNSAFE_BUILD})

# export the submodule flag so that crypto knows it's being built as a submodule
if(${CMAKE_VERSION} VERSION_LESS "3.11")
    MESSAGE(STATUS "FetchContent not available in your CMake version (min 3.11). It is required for you to use git submodules")
    set( USE_CRYPTO_SUBMODULE ON CACHE BOOL "Are we building using submodule or FetchContent" )
else(${CMAKE_VERSION} VERSION_LESS "3.11")
    set( USE_CRYPTO_SUBMODULE OFF CACHE BOOL "Are we building using submodule or FetchContent" )
endif(${CMAKE_VERSION} VERSION_LESS "3.11")

# LOG OPTIONS

MESSAGE("---------------- MBEDTLS OPTIONS. ----------------")

#General
MESSAGE(STATUS "MBEDTLS_PROJECT          : " ${MBEDTLS_PROJECT})
MESSAGE(STATUS "MBEDTLS_VERSION          : " ${MBEDTLS_VERSION})
MESSAGE(STATUS "MBEDTLS_TARGET           : " ${MBEDTLS_TARGET})
MESSAGE(STATUS "MBEDTLS_BUILD_SHARED     : " ${MBEDTLS_BUILD_SHARED})
MESSAGE(STATUS "MBEDTLS_FOLDER_PREFIX    : " ${MBEDTLS_FOLDER_PREFIX})
MESSAGE(STATUS "MBEDTLS_UNSAFE_BUILD     : " ${MBEDTLS_UNSAFE_BUILD})

# Tests
MESSAGE(STATUS "MBEDTLS_ENABLE_TESTS     : " ${MBEDTLS_ENABLE_TESTS})
IF(MBEDTLS_ENABLE_TESTS)
MESSAGE(STATUS "MBEDTLS_TESTS_PREFIX     : " ${MBEDTLS_TESTS_PREFIX})
ENDIF(MBEDTLS_ENABLE_TESTS)

# Examples
MESSAGE(STATUS "MBEDTLS_ENABLE_EXAMPLES  : " ${MBEDTLS_ENABLE_EXAMPLES})
IF(MBEDTLS_ENABLE_EXAMPLES)
MESSAGE(STATUS "MBEDTLS_EXAMPLES_PREFIX  : " ${MBEDTLS_EXAMPLES_PREFIX})
ENDIF(MBEDTLS_ENABLE_EXAMPLES)

# Install
MESSAGE(STATUS "MBEDTLS_ENABLE_INSTALL   : " ${MBEDTLS_ENABLE_INSTALL})
IF(MBEDTLS_ENABLE_INSTALL)
MESSAGE(STATUS "MBEDTLS_INSTALL_PREFIX   : " ${MBEDTLS_INSTALL_PREFIX})
ENDIF(MBEDTLS_ENABLE_INSTALL)

MESSAGE("---------------- DONE WITH OPTIONS. -----------------")
MESSAGE("                                                     ")

# General
SET( MBEDCRYPTO_PROJECT "mbedcrypto" CACHE STRING "Project Name")
SET( MBEDCRYPTO_TARGET "${MBEDCRYPTO_PROJECT}" CACHE STRING "mbedcrypto library name" )
SET( MBEDCRYPTO_VERSION "1.1.1" CACHE STRING "mbedcrypto current version, this is only decorative and will not configure any files" FORCE )
SET( MBEDCRYPTO_BUILD_SHARED OFF CACHE BOOL "Build as a shared library (ON) or as static (OFF)" )
SET( MBEDCRYPTO_FOLDER_PREFIX ${MBEDCRYPTO_TARGET} CACHE STRING "Prefix folder for all mbedcrypto generated targets in generated project (only decorative)" )
SET( MBEDCRYPTO_UNSAFE_BUILD OFF CACHE BOOL "Allow unsafe builds. These builds ARE NOT SECURE" )
SET( MBEDCRYPTO_LINK_WITH_PTHREAD OFF CACHE BOOL "Explicitly link mbed crypto library to pthread." )

# Tests
SET( MBEDCRYPTO_ENABLE_TESTS OFF CACHE BOOL "Create or not a target for test (compatible with CTests)" )
SET( MBEDCRYPTO_TESTS_PREFIX ${MBEDCRYPTO_TARGET} CACHE STRING "Prefix for all mbedcrypto tests" )
IF(NOT ${MBEDCRYPTO_TESTS_PREFIX} STREQUAL "")
    SET( MBEDCRYPTO_TESTS_PREFIX_ "${MBEDCRYPTO_TESTS_PREFIX}_" )
ELSE(NOT ${MBEDCRYPTO_TESTS_PREFIX} STREQUAL "")
    SET( MBEDCRYPTO_TESTS_PREFIX_ "" )
ENDIF(NOT ${MBEDCRYPTO_TESTS_PREFIX} STREQUAL "")

# Examples
SET( MBEDCRYPTO_ENABLE_EXAMPLES OFF CACHE BOOL "Create or not a target for examples" )
SET( MBEDCRYPTO_EXAMPLES_PREFIX ${MBEDCRYPTO_TARGET} CACHE STRING "Prefix for all mbedcrypto tests" )
IF(NOT ${MBEDCRYPTO_EXAMPLES_PREFIX} STREQUAL "")
    SET( MBEDCRYPTO_EXAMPLES_PREFIX_ "${MBEDCRYPTO_EXAMPLES_PREFIX}_" )
ELSE(NOT ${MBEDCRYPTO_EXAMPLES_PREFIX} STREQUAL "")
    SET( MBEDCRYPTO_EXAMPLES_PREFIX_ "" )
ENDIF(NOT ${MBEDCRYPTO_EXAMPLES_PREFIX} STREQUAL "")

# Install
SET( MBEDCRYPTO_ENABLE_INSTALL OFF CACHE BOOL "Create or not a target for install" )
SET( MBEDCRYPTO_INSTALL_PREFIX ${MBEDCRYPTO_TARGET} CACHE STRING "Prefix for all mbedcrypto headers in the install folder" )

# LOG OPTIONS

MESSAGE("---------------- MBEDCRYPTO OPTIONS. ----------------")

#General
MESSAGE(STATUS "MBEDCRYPTO_PROJECT          : " ${MBEDCRYPTO_PROJECT})
MESSAGE(STATUS "MBEDCRYPTO_VERSION          : " ${MBEDCRYPTO_VERSION})
MESSAGE(STATUS "MBEDCRYPTO_TARGET           : " ${MBEDCRYPTO_TARGET})
MESSAGE(STATUS "MBEDTLS_DIR                 : " ${MBEDTLS_DIR})
MESSAGE(STATUS "MBEDCRYPTO_BUILD_SHARED     : " ${MBEDCRYPTO_BUILD_SHARED})
MESSAGE(STATUS "MBEDCRYPTO_FOLDER_PREFIX    : " ${MBEDCRYPTO_FOLDER_PREFIX})
MESSAGE(STATUS "MBEDCRYPTO_UNSAFE_BUILD     : " ${MBEDCRYPTO_UNSAFE_BUILD})

# Tests
MESSAGE(STATUS "MBEDCRYPTO_ENABLE_TESTS     : " ${MBEDCRYPTO_ENABLE_TESTS})
IF(MBEDCRYPTO_ENABLE_TESTS)
MESSAGE(STATUS "MBEDCRYPTO_TESTS_PREFIX     : " ${MBEDCRYPTO_TESTS_PREFIX})
ENDIF(MBEDCRYPTO_ENABLE_TESTS)

# Examples
MESSAGE(STATUS "MBEDCRYPTO_ENABLE_EXAMPLES  : " ${MBEDCRYPTO_ENABLE_EXAMPLES})
IF(MBEDCRYPTO_ENABLE_EXAMPLES)
MESSAGE(STATUS "MBEDCRYPTO_EXAMPLES_PREFIX  : " ${MBEDCRYPTO_EXAMPLES_PREFIX})
ENDIF(MBEDCRYPTO_ENABLE_EXAMPLES)

# Install
MESSAGE(STATUS "MBEDCRYPTO_ENABLE_INSTALL   : " ${MBEDCRYPTO_ENABLE_INSTALL})
IF(MBEDCRYPTO_ENABLE_INSTALL)
MESSAGE(STATUS "MBEDCRYPTO_INSTALL_PREFIX   : " ${MBEDCRYPTO_INSTALL_PREFIX})
ENDIF(MBEDCRYPTO_ENABLE_INSTALL)

MESSAGE("---------------- DONE WITH OPTIONS. -----------------")
MESSAGE("                                                     ")


# ┌──────────────────────────────────────────────────────────────────┐
# │                       DEPENDENCIES                               │
# └──────────────────────────────────────────────────────────────────┘

set(MBEDTLS_DIR ${CMAKE_CURRENT_SOURCE_DIR} CACHE STRING "" FORCE)

string(REGEX MATCH "Clang" CMAKE_COMPILER_IS_CLANG "${CMAKE_C_COMPILER_ID}")
string(REGEX MATCH "GNU" CMAKE_COMPILER_IS_GNU "${CMAKE_C_COMPILER_ID}")
string(REGEX MATCH "IAR" CMAKE_COMPILER_IS_IAR "${CMAKE_C_COMPILER_ID}")
string(REGEX MATCH "MSVC" CMAKE_COMPILER_IS_MSVC "${CMAKE_C_COMPILER_ID}")

# the test suites currently have compile errors with MSVC
option(ENABLE_TESTING "Build mbed TLS tests." ${MBEDTLS_ENABLE_TESTS})

# Warning string - created as a list for compatibility with CMake 2.8
set(WARNING_BORDER "*******************************************************\n")
set(NULL_ENTROPY_WARN_L1 "****  WARNING!  MBEDTLS_TEST_NULL_ENTROPY defined!\n")
set(NULL_ENTROPY_WARN_L2 "****  THIS BUILD HAS NO DEFINED ENTROPY SOURCES\n")
set(NULL_ENTROPY_WARN_L3 "****  AND IS *NOT* SUITABLE FOR PRODUCTION USE\n")

set(NULL_ENTROPY_WARNING "${WARNING_BORDER}"
                         "${NULL_ENTROPY_WARN_L1}"
                         "${NULL_ENTROPY_WARN_L2}"
                         "${NULL_ENTROPY_WARN_L3}"
                         "${WARNING_BORDER}")

set(CTR_DRBG_128_BIT_KEY_WARN_L1 "****  WARNING!  MBEDTLS_CTR_DRBG_USE_128_BIT_KEY defined!\n")
set(CTR_DRBG_128_BIT_KEY_WARN_L2 "****  Using 128-bit keys for CTR_DRBG limits the security of generated\n")
set(CTR_DRBG_128_BIT_KEY_WARN_L3 "****  keys and operations that use random values generated to 128-bit security\n")

set(CTR_DRBG_128_BIT_KEY_WARNING "${WARNING_BORDER}"
                         "${CTR_DRBG_128_BIT_KEY_WARN_L1}"
                         "${CTR_DRBG_128_BIT_KEY_WARN_L2}"
                         "${CTR_DRBG_128_BIT_KEY_WARN_L3}"
                         "${WARNING_BORDER}")

find_package(PythonInterp)
find_package(Perl)
if(PERL_FOUND)

    # If 128-bit keys are configured for CTR_DRBG, display an appropriate warning
    execute_process(COMMAND ${PERL_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/scripts/config.pl -f ${CMAKE_CURRENT_SOURCE_DIR}/include/mbedtls/config.h get MBEDTLS_CTR_DRBG_USE_128_BIT_KEY
                        RESULT_VARIABLE result)
    if(${result} EQUAL 0)
        message(WARNING ${CTR_DRBG_128_BIT_KEY_WARNING})
    endif()

    # If NULL Entropy is configured, display an appropriate warning
    execute_process(COMMAND ${PERL_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/scripts/config.pl -f ${CMAKE_CURRENT_SOURCE_DIR}/include/mbedtls/config.h get MBEDTLS_TEST_NULL_ENTROPY
                        RESULT_VARIABLE result)
    if(${result} EQUAL 0)
        message(WARNING ${NULL_ENTROPY_WARNING})

        if(NOT UNSAFE_BUILD)
            message(FATAL_ERROR "\
\n\
Warning! You have enabled MBEDTLS_TEST_NULL_ENTROPY. \
This option is not safe for production use and negates all security \
It is intended for development use only. \
\n\
To confirm you want to build with this option, re-run cmake with the \
option: \n\
  cmake -DUNSAFE_BUILD=ON ")

            return()
        endif()
    endif()
endif()

set(CMAKE_BUILD_TYPE ${CMAKE_BUILD_TYPE}
    CACHE STRING "Choose the type of build: None Debug Release Coverage ASan ASanDbg MemSan MemSanDbg Check CheckFull"
    FORCE)

# Create a symbolic link from ${base_name} in the binary directory
# to the corresponding path in the source directory.
function(link_to_source base_name)
    # Get OS dependent path to use in `execute_process`
    if (CMAKE_HOST_WIN32)
        #mklink is an internal command of cmd.exe it can only work with \
        string(REPLACE "/" "\\" link "${CMAKE_CURRENT_BINARY_DIR}/${base_name}")
        string(REPLACE "/" "\\" target "${CMAKE_CURRENT_SOURCE_DIR}/${base_name}")
    else()
        set(link "${CMAKE_CURRENT_BINARY_DIR}/${base_name}")
        set(target "${CMAKE_CURRENT_SOURCE_DIR}/${base_name}")
    endif()

    if (NOT EXISTS ${link})
        if (CMAKE_HOST_UNIX)
            set(command ln -s ${target} ${link})
        else()
            if (IS_DIRECTORY ${target})
                set(command cmd.exe /c mklink /j ${link} ${target})
            else()
                set(command cmd.exe /c mklink /h ${link} ${target})
            endif()
        endif()

        execute_process(COMMAND ${command}
            RESULT_VARIABLE result
            ERROR_VARIABLE output)

        if (NOT ${result} EQUAL 0)
            message(FATAL_ERROR "Could not create symbolic link for: ${target} --> ${output}")
        endif()
    endif()
endfunction(link_to_source)

string(REGEX MATCH "Clang" CMAKE_COMPILER_IS_CLANG "${CMAKE_C_COMPILER_ID}")

if(CMAKE_COMPILER_IS_GNU)
    # some warnings we want are not available with old GCC versions
    # note: starting with CMake 2.8 we could use CMAKE_C_COMPILER_VERSION
    execute_process(COMMAND ${CMAKE_C_COMPILER} -dumpversion
                    OUTPUT_VARIABLE GCC_VERSION)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -W -Wdeclaration-after-statement -Wwrite-strings")
    if (GCC_VERSION VERSION_GREATER 4.5 OR GCC_VERSION VERSION_EQUAL 4.5)
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wlogical-op")
    endif()
    if (GCC_VERSION VERSION_GREATER 4.8 OR GCC_VERSION VERSION_EQUAL 4.8)
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wshadow")
    endif()
    set(CMAKE_C_FLAGS_RELEASE     "-O2")
    set(CMAKE_C_FLAGS_DEBUG       "-O0 -g3")
    set(CMAKE_C_FLAGS_COVERAGE    "-O0 -g3 --coverage")
    set(CMAKE_C_FLAGS_ASAN        "-Werror -fsanitize=address -fno-common -O3")
    set(CMAKE_C_FLAGS_ASANDBG     "-Werror -fsanitize=address -fno-common -O1 -g3 -fno-omit-frame-pointer -fno-optimize-sibling-calls ")
    set(CMAKE_C_FLAGS_CHECK       "-Werror -Os")
    set(CMAKE_C_FLAGS_CHECKFULL   "${CMAKE_C_FLAGS_CHECK} -Wcast-qual")
endif(CMAKE_COMPILER_IS_GNU)

if(CMAKE_COMPILER_IS_CLANG)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -W -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -Wimplicit-fallthrough -Wshadow")
    set(CMAKE_C_FLAGS_RELEASE     "-O2")
    set(CMAKE_C_FLAGS_DEBUG       "-O0 -g3")
    set(CMAKE_C_FLAGS_COVERAGE    "-O0 -g3 --coverage")
    set(CMAKE_C_FLAGS_ASAN        "-Werror -fsanitize=address -fno-common -fsanitize=undefined -fno-sanitize-recover=all -O3")
    set(CMAKE_C_FLAGS_ASANDBG     "-Werror -fsanitize=address -fno-common -fsanitize=undefined -fno-sanitize-recover=all -O1 -g3 -fno-omit-frame-pointer -fno-optimize-sibling-calls ")
    set(CMAKE_C_FLAGS_MEMSAN      "-Werror -fsanitize=memory -O3")
    set(CMAKE_C_FLAGS_MEMSANDBG   "-Werror -fsanitize=memory -O1 -g3 -fno-omit-frame-pointer -fno-optimize-sibling-calls -fsanitize-memory-track-origins=2")
    set(CMAKE_C_FLAGS_CHECK       "-Werror -Os")
endif(CMAKE_COMPILER_IS_CLANG)

if(CMAKE_COMPILER_IS_IAR)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} --warn_about_c_style_casts --warnings_are_errors -Ohz")
endif(CMAKE_COMPILER_IS_IAR)

if(CMAKE_COMPILER_IS_MSVC)
    # Strictest warnings, and treat as errors
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /W3")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /WX")
endif(CMAKE_COMPILER_IS_MSVC)

if(CMAKE_BUILD_TYPE STREQUAL "Coverage")
    if(CMAKE_COMPILER_IS_GNU OR CMAKE_COMPILER_IS_CLANG)
        set(CMAKE_SHARED_LINKER_FLAGS "--coverage")
    endif(CMAKE_COMPILER_IS_GNU OR CMAKE_COMPILER_IS_CLANG)
endif(CMAKE_BUILD_TYPE STREQUAL "Coverage")

if(LIB_INSTALL_DIR)
else()
    set(LIB_INSTALL_DIR lib)
endif()

if(ENABLE_ZLIB_SUPPORT)
    find_package(ZLIB)

    if(ZLIB_FOUND)
        include_directories(${ZLIB_INCLUDE_DIR})
    endif(ZLIB_FOUND)
endif(ENABLE_ZLIB_SUPPORT)

add_subdirectory(library)
add_subdirectory(include)
IF(USE_CRYPTO_SUBMODULE)
    add_subdirectory(crypto/library)
    add_subdirectory(crypto/include)
ENDIF(USE_CRYPTO_SUBMODULE)

if(ENABLE_PROGRAMS OR MBEDTLS_ENABLE_EXAMPLES)
    add_subdirectory(programs)
endif()

ADD_CUSTOM_TARGET(${MBEDTLS_EXAMPLES_PREFIX_}apidoc
    COMMAND doxygen mbedtls.doxyfile
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/doxygen)
SET_TARGET_PROPERTIES(${MBEDTLS_EXAMPLES_PREFIX_}apidoc PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Doc)

if(ENABLE_TESTING OR MBEDTLS_ENABLE_TESTS)
    enable_testing()

    add_subdirectory(tests)
    IF(USE_CRYPTO_SUBMODULE)
        add_subdirectory(crypto/tests)
    ENDIF(USE_CRYPTO_SUBMODULE)

    # additional convenience targets for Unix only
    if(UNIX)

        ADD_CUSTOM_TARGET(${MBEDTLS_TESTS_PREFIX_}covtest
            COMMAND make test
            COMMAND programs/test/selftest
            COMMAND tests/compat.sh
            COMMAND tests/ssl-opt.sh
        )
        SET_TARGET_PROPERTIES(${MBEDTLS_TESTS_PREFIX_}covtest PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Tests)

        ADD_CUSTOM_TARGET(${MBEDTLS_TESTS_PREFIX_}lcov
            COMMAND rm -rf Coverage
            COMMAND lcov --capture --initial --directory library/CMakeFiles/mbedtls.dir -o files.info
            COMMAND lcov --capture --directory library/CMakeFiles/mbedtls.dir -o tests.info
            COMMAND lcov --add-tracefile files.info --add-tracefile tests.info -o all.info
            COMMAND lcov --remove all.info -o final.info '*.h'
            COMMAND gendesc tests/Descriptions.txt -o descriptions
            COMMAND genhtml --title "mbed TLS" --description-file descriptions --keep-descriptions --legend --no-branch-coverage -o Coverage final.info
            COMMAND rm -f files.info tests.info all.info final.info descriptions
        )
        SET_TARGET_PROPERTIES(${MBEDTLS_TESTS_PREFIX_}lcov PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Tests)

        ADD_CUSTOM_TARGET(${MBEDTLS_TESTS_PREFIX_}memcheck
            COMMAND sed -i.bak s+/usr/bin/valgrind+`which valgrind`+ DartConfiguration.tcl
            COMMAND ctest -O memcheck.log -D ExperimentalMemCheck
            COMMAND tail -n1 memcheck.log | grep 'Memory checking results:' > /dev/null
            COMMAND rm -f memcheck.log
            COMMAND mv DartConfiguration.tcl.bak DartConfiguration.tcl
        )
        SET_TARGET_PROPERTIES(${MBEDTLS_TESTS_PREFIX_}memcheck PROPERTIES FOLDER ${MBEDTLS_FOLDER_PREFIX}/Tests)
    endif(UNIX)

    # Make scripts needed for testing available in an out-of-source build.
    if (NOT ${CMAKE_CURRENT_BINARY_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR})
        link_to_source(scripts)
        # Copy (don't link) DartConfiguration.tcl, needed for memcheck, to
        # keep things simple with the sed commands in the memcheck target.
        configure_file(${CMAKE_CURRENT_SOURCE_DIR}/DartConfiguration.tcl
                    ${CMAKE_CURRENT_BINARY_DIR}/DartConfiguration.tcl COPYONLY)
    endif()
endif()
