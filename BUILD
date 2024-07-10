load("@build_bazel_rules_swift//swift:swift.bzl", "swift_library")

cc_library(
    name = "CYaml",
    srcs = glob([
        "Sources/CYaml/src/*.c",
        "Sources/CYaml/src/*.h",
    ]),
    hdrs = ["Sources/CYaml/include/yaml.h"],
    aspect_hints = ["@build_bazel_rules_swift//swift:auto_module"],
    # Requires because of https://github.com/bazelbuild/bazel/pull/10143 otherwise host transition builds fail
    copts = ["-fPIC"],
    includes = ["Sources/CYaml/include"],
    linkstatic = True,
    visibility = ["//Tests:__subpackages__"],
)

swift_library(
    name = "Yams",
    srcs = glob(["Sources/Yams/*.swift"]),
    copts = ["-DSWIFT_PACKAGE"],
    module_name = "Yams",
    visibility = ["//visibility:public"],
    deps = ["//:CYaml"],
)
