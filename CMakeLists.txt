cmake_minimum_required(VERSION 3.11)
add_library(httplib STATIC httplib.cpp)
if (DEFINED CPPHTTPLIB_OPENSSL_DIR) 
  target_include_directories(httplib PRIVATE 
    "${CPPHTTPLIB_OPENSSL_DIR}/include"
  )
  target_link_directories(
    httplib PRIVATE 
    "${CPPHTTPLIB_OPENSSL_DIR}/lib"
  )
endif()
target_compile_definitions(httplib PRIVATE CPPHTTPLIB_OPENSSL_SUPPORT)
