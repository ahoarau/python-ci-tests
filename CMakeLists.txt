cmake_minimum_required(VERSION 3.22)
project(py)

include(FetchContent)
FetchContent_Declare(
  jrl-cmakemodules
  GIT_REPOSITORY https://github.com/ahoarau/jrl-cmakemodules
  GIT_TAG jrl-next
)
FetchContent_MakeAvailable(jrl-cmakemodules)

jrl_find_python(3.8 COMPONENTS Interpreter Development.Module NumPy)
