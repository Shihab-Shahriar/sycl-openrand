set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -fsycl")
set(CMAKE_BUILD_TYPE "RelWithDebInfo")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS}")
add_executable (nbody GSimulation.cpp main.cpp)
target_link_libraries(nbody OpenCL sycl)
if(WIN32)
        add_custom_target (run nbody.exe)
else()
	add_custom_target (run ./nbody)
endif()


include(FetchContent)
FetchContent_Declare(
  crng
  GIT_REPOSITORY https://github.com/msu-sparta/OpenRAND.git
  GIT_TAG        main
)

FetchContent_MakeAvailable(crng)
target_include_directories(nbody PUBLIC ${crng_SOURCE_DIR}/include)