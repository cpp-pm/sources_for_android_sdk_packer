# Copyright (c) 2018, Ruslan Baratov
# All rights reserved.

cmake_minimum_required(VERSION 3.3)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.20.40.tar.gz"
    SHA1 "a500979296b4b6b1542a2881151ceb9c984f3e36"
)

project(sources_for_android_sdk_packer)

hunter_add_package(android_sdk_packer)

# android_sdk_packer_unified_install
find_package(android_sdk_packer CONFIG REQUIRED)

hunter_add_package(Sources-for-Android-SDK)

set(android_sdk_version "${HUNTER_Sources-for-Android-SDK_VERSION}")

file(GLOB x "${SOURCES-FOR-ANDROID-SDK_ROOT}/*")
android_sdk_packer_unified_install(
    OBJECTS ${x}
    DESTINATION "sources/android-${android_sdk_version}"
)
