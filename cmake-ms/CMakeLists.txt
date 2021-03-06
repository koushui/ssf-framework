cmake_minimum_required(VERSION 2.8)

# --- Special settings to Windows platform
if (WIN32)
  include(MSVCStaticRuntime)
  include(HelpersIdeTarget)

  # --- Icon path
  set(SSF_FRAMEWORK_EXEC_FLAG "RUNTIME_STATIC")

  # --- Boost platform requirements
  list(APPEND SSF_FRAMEWORK_BOOST_PLATFORM_FLAGS "RUNTIME_STATIC")
  list(APPEND SSF_FRAMEWORK_BOOST_PLATFORM_COMPONENTS "context" "coroutine")
    
  # --- OpenSSL platform requirements
  list(APPEND SSF_FRAMEWORK_OPENSSL_PLATFORM_FLAGS "RUNTIME_STATIC")
  
  # --- Flags for compilation
  add_definitions(-D_WIN32_WINNT=0x0501)
  if (MSVC)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /bigobj /wd4503")
    add_definitions(-D_SCL_SECURE_NO_WARNINGS)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
  endif(MSVC)
endif (WIN32)

