# Description:
#   Tests for whitelisting mechanism for rolling out and deprecating pieces of Blaze functionality.

load("@rules_java//java:defs.bzl", "java_library", "java_test")

package(
    default_testonly = 1,
    default_visibility = ["//src:__subpackages__"],
)

filegroup(
    name = "srcs",
    testonly = 0,
    srcs = glob(["*"]),
)

java_library(
    name = "WhitelistUtil",
    testonly = 1,
    srcs = ["WhitelistDummyRule.java"],
    deps = [
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/main/java/com/google/devtools/build/lib/actions",
        "//src/main/java/com/google/devtools/build/lib/cmdline",
        "//src/main/java/com/google/devtools/build/lib/collect/nestedset",
        "//src/main/java/com/google/devtools/build/lib/packages",
        "//src/test/java/com/google/devtools/build/lib/analysis/util",
    ],
)

# Description:
#   Tests for whitelisting mechanism for rolling out and deprecating pieces of Bazel functionality.
java_test(
    name = "WhitelistingTests",
    srcs = [
        "WhitelistCachingTest.java",
        "WhitelistTest.java",
    ],
    test_class = "com.google.devtools.build.lib.AllTests",
    runtime_deps = [
        "//src/test/java/com/google/devtools/build/lib:test_runner",
    ],
    deps = [
        ":WhitelistUtil",
        "//src/main/java/com/google/devtools/build/lib:build-base",
        "//src/test/java/com/google/devtools/build/lib/analysis/util",
        "//src/test/java/com/google/devtools/build/lib/testutil",
        "//src/test/java/com/google/devtools/build/lib/testutil:JunitUtils",
        "//third_party:junit4",
    ],
)

test_suite(
    name = "windows_tests",
    tags = [
        "-no_windows",
        "-slow",
    ],
)

test_suite(
    name = "all_windows_tests",
    tests = [
        ":windows_tests",
    ],
)
