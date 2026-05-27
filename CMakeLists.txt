cmake_minimum_required(VERSION 3.11)
add_library(httplib STATIC httplib.cpp)
if (DEFINED CPPHTTPLIB_OPENSSL_DIR) 
  message(STATUS "OpenSSL dir provided: ${CPPHTTPLIB_OPENSSL_DIR}")
  target_include_directories(httplib PRIVATE 
    "${CPPHTTPLIB_OPENSSL_DIR}/include"
  )
  target_link_directories(
    httplib PRIVATE 
   "${CPPHTTPLIB_OPENSSL_DIR}/lib"
  )
endif()
if (DEFINED CPPHTTPLIB_OPENSSL_LIBS)
  target_link_libraries(httplib PRIVATE ${CPPHTTPLIB_OPENSSL_LIBS})
endif()
target_compile_definitions(
  httplib PRIVATE 
  CPPHTTPLIB_NO_PLATFORM_COMPATIBILITY_CHECK 
  CPPHTTPLIB_OPENSSL_SUPPORT
)
