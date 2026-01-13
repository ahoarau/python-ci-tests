cmake_minimum_required(VERSION 3.22)
project(py)

set(
  JRL_CMAKEMODULES_USE_V2
  ON
  CACHE BOOL
  "Use jrl-cmakemodules v2 on https://github.com/jrl-umi3218/jrl-cmakemodules"
)
include(FetchContent)
FetchContent_Declare(
  jrl-cmakemodules
  GIT_REPOSITORY https://github.com/ahoarau/jrl-cmakemodules
  GIT_TAG jrl-next
)
FetchContent_MakeAvailable(jrl-cmakemodules)

jrl_option(BUILD_TESTING "Build the tests" OFF)
jrl_option(BUILD_EXAMPLES "Build the examples" OFF)
jrl_option(BUILD_BENCHMARKS "Build the benchmarks" OFF)
jrl_option(BUILD_DOCUMENTATION "Build the documentation." OFF)
jrl_option(BUILD_PYTHON_INTERFACE "Build the Python bindings" OFF)

jrl_cmake_dependent_option(
  INSTALL_DOCUMENTATION
  "Install the documentation"
  ON
  BUILD_DOCUMENTATION
  OFF
)

jrl_find_python(3.8 COMPONENTS Interpreter Development.Module NumPy)

jrl_print_dependencies_summary()
jrl_print_options_summary()
