# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.
add_definitions(-Wno-deprecated)

add_library( # Sets the name of the library.
        luabridge

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        src/main/jni/luabridge.cpp
        src/main/jni/shell.cpp
        src/main/jni/LuaEngine.cpp
        src/main/jni/LuaTask.cpp
        src/main/jni/JniManager.cpp
        src/main/jni/utils/LuaUtils.cpp

        src/main/jni/lua/lapi.c
        src/main/jni/lua/lauxlib.c
        src/main/jni/lua/lbaselib.c
        src/main/jni/lua/lbitlib.c
        src/main/jni/lua/lcode.c
        src/main/jni/lua/lcorolib.c
        src/main/jni/lua/lctype.c
        src/main/jni/lua/ldblib.c
        src/main/jni/lua/ldebug.c
        src/main/jni/lua/ldo.c
        src/main/jni/lua/ldump.c
        src/main/jni/lua/lfunc.c
        src/main/jni/lua/lgc.c
        src/main/jni/lua/linit.c
        src/main/jni/lua/liolib.c
        src/main/jni/lua/llex.c
        src/main/jni/lua/lmathlib.c
        src/main/jni/lua/lmem.c
        src/main/jni/lua/loadlib.c
        src/main/jni/lua/lobject.c
        src/main/jni/lua/lopcodes.c
        src/main/jni/lua/loslib.c
        src/main/jni/lua/lparser.c
        src/main/jni/lua/lstate.c
        src/main/jni/lua/lstring.c
        src/main/jni/lua/lstrlib.c
        src/main/jni/lua/ltable.c
        src/main/jni/lua/ltablib.c
        src/main/jni/lua/ltm.c
        src/main/jni/lua/lua.c
        src/main/jni/lua/lundump.c
        src/main/jni/lua/lutf8lib.c
        src/main/jni/lua/lvm.c
        src/main/jni/lua/lzio.c)

# Searches for a specified prebuilt library and stores the path as a
# variable. Because CMake includes system libraries in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
        log-lib

        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
        luabridge

        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})