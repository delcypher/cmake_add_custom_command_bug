add_executable(simple_test simple.cpp)
target_link_libraries(simple_test PRIVATE foolib)

# FIXME: This seems like a bug in CMake, this custom
# command does not fire when foolib gets built
# Tried with 2.8.12.2
#
# With CMake 3.2.3 I get a warning about CMP0040
# (target in the TARGET of signature of add_custom_command()
# must exist).
#
# This doesn't make sense since we can read properties of the foolib target so
# it MUST EXIST!!!
add_custom_command(TARGET foolib
                   POST_BUILD
                   COMMAND echo XXXXXXXX
                   COMMAND simple_test
                   COMMENT "Running simple_test")

# Demonstrate that the foolib target does exist in this scope!
get_target_property(foolib_loc foolib LOCATION)

message(STATUS "The reported location of the foolib target is ${foolib_loc}")
