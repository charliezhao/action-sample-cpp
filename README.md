
![example workflow name](https://github.com/dankernel/action-sample-cpp/workflows/CMake/badge.svg)

# Run
```
mkdir build
cd build
cmake ../src
make
```

# cmake.yml
```
name: CMake

on: [push]

env:
  # Customize the CMake build type here (Release, Debug, RelWithDebInfo, etc.)
  BUILD_TYPE: Release

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Create Build Environment
      run: cmake -E make_directory ${{github.workspace}}/build

    - name: Configure CMake
      shell: bash
      working-directory: ${{github.workspace}}/build
      run: |
        echo $GITHUB_WORKSPACE
        cmake $GITHUB_WORKSPACE/src -DCMAKE_BUILD_TYPE=$BUILD_TYPE
    - name: Build
      working-directory: ${{github.workspace}}/build
      shell: bash
      run: |
        echo $GITHUB_WORKSPACE
        ls $GITHUB_WORKSPACE
        cmake --build . --config $BUILD_TYPE
    - name: Test
      working-directory: ${{github.workspace}}/build
      shell: bash
      run: ctest -C $BUILD_TYPE
```
