load("@rules_java//java:defs.bzl", "java_library", "java_test")

# Description:
#   Tests of the testing tools for the devtools-common options parser.
package(
    default_testonly = 1,
    default_visibility = ["//visibility:private"],
)

licenses(["notice"])  # Apache 2.0

filegroup(
    name = "srcs",
    testonly = 0,
    srcs = glob(
        ["**"],
    ),
    visibility = ["//src/test/java/com/google/devtools/common/options:__pkg__"],
)

java_library(
    name = "OptionsTesterTest_lib",
    srcs = glob(["*.java"]),
    deps = [
        "//src/main/java/com/google/devtools/common/options",
        "//src/main/java/com/google/devtools/common/options/testing",
        "//src/test/java/com/google/devtools/build/lib/testutil",
        "//src/test/java/com/google/devtools/build/lib/testutil:JunitUtils",
        "//src/test/java/com/google/devtools/build/lib/testutil:TestSuite",
        "//third_party:guava",
        "//third_party:guava-testlib",
        "//third_party:junit4",
        "//third_party:truth",
    ],
)

java_test(
    name = "OptionsTesterTest",
    test_class = "com.google.devtools.common.options.testing.AllTests",
    runtime_deps = [":OptionsTesterTest_lib"],
)

test_suite(
    name = "windows_tests",
    tags = [
        "-no_windows",
        "-slow",
    ],
    visibility = ["//visibility:private"],
)

test_suite(
    name = "all_windows_tests",
    tests = [
        ":windows_tests",
    ],
    visibility = ["//src/test/java/com/google/devtools/common/options:__pkg__"],
)
