add_executable(simple_test simple.cpp)
target_link_libraries(simple_test PRIVATE foolib)

# FIXME: This seems like a bug in CMake, this custom
# command does not fire when foolib gets built
# Tried with 2.8.12.2
add_custom_command(TARGET foolib
                   POST_BUILD
                   COMMAND echo XXXXXXXX
                   COMMAND simple_test
                   COMMENT "Running simple_test")

