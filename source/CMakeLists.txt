set(BUILD_DIR ${CMAKE_BINARY_DIR}/build${CMAKE_SYSTEM_PROCESSOR})

set(C_SRCS
    curve25519_mehdi.c
    curve25519_order.c
    curve25519_utils.c
    curve25519_dh.c
    ed25519_sign.c
    ed25519_verify.c
    sha512.c
    custom_blind.c
    ../custom/random.c
)

set(CPP_SRCS
    ../cpp/ed25519.cpp
)

add_library(curve25519 STATIC ${C_SRCS} ${CPP_SRCS})

target_include_directories(curve25519 PUBLIC custom ../include)

target_compile_options(curve25519 PRIVATE
    -Wall
    -O2
    $<$<COMPILE_LANGUAGE:CXX>:-static-libgcc>
)
