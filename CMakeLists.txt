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
find_package(Python 3.8 REQUIRED COMPONENTS Interpreter Development.Module NumPy)
jrl_find_python(3.8 COMPONENTS Interpreter Development.Module NumPy)
