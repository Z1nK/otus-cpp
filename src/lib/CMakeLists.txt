add_library(helloworld lib.cpp)

set_target_properties(helloworld PROPERTIES
    CXX_STANDARD 14
    CXX_STANDARD_REQUIRED ON
)

target_include_directories(helloworld PUBLIC  
  $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/..>
  $<BUILD_INTERFACE:${PROJ_AUTOGEN_DIR}>
  )

if (MSVC)
    target_compile_options(helloworld PRIVATE /W4)
else()
    target_compile_options(helloworld PRIVATE -Wall -Wextra -pedantic -Werror)
endif()