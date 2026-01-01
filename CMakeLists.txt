# Cuckoo Cycle library for Monero integration

cmake_minimum_required(VERSION 3.5)

project(cuckoo)

# Add Cuckoo Cycle crypto sources
set(CUCKOO_CRYPTO_SOURCES
    src/crypto/blake2b-ref.c
)

# Create cuckoo library
add_library(cuckoo STATIC ${CUCKOO_CRYPTO_SOURCES})

# Include directories
target_include_directories(cuckoo PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${CMAKE_CURRENT_SOURCE_DIR}/src/crypto
)

# Set compile options
if(MSVC)
    target_compile_options(cuckoo PRIVATE /W3)
else()
    target_compile_options(cuckoo PRIVATE -Wall -Wextra)
endif()

# Export include directories
set(CUCKOO_INCLUDE_DIRS 
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${CMAKE_CURRENT_SOURCE_DIR}/src/crypto
    PARENT_SCOPE
)
