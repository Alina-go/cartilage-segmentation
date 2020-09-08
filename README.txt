cmake
  -DCMAKE_CXX_COMPILER:STRING="C:/Program Files (x86)/Microsoft Visual Studio 14.0/VC/BIN/amd64/cl.exe"
  -DCMAKE_CXX_FLAGS="$(CMAKE_CXX_FLAGS) /I \"C:/Program Files (x86)/Microsoft Visual Studio 14.0/VC/include\""
  -DCMAKE_EXE_LINKER_FLAGS="$(CMAKE_EXE_LINKER_FLAGS) -LIBPATH:\"C:/Program Files (x86)/Microsoft Visual Studio 14.0/VC/lib/amd64\""
  -DOpenCASCADE_DIR="C:/OpenCASCADE-7.4.0-vc14-64/opencascade-7.4.0/cmake"
  ..\CartilageSegmentation\CMakeLists.txt
  -A x64
  
cmake --build ..\CartilageSegmentation\CMakeLists.txt