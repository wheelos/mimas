## Auto generated by `proto_build_generator.py`
load("@rules_proto//proto:defs.bzl", "proto_library")
load("@rules_cc//cc:defs.bzl", "cc_proto_library")

package(default_visibility = ["//visibility:public"])

cc_proto_library(
    name = "simple_cc_proto",
    deps = [
        ":simple_proto",
    ],
)

proto_library(
    name = "simple_proto",
    srcs = ["simple.proto"],
    deps = [
        "@wheelos_common_msgs//common_msgs/basic_msgs:header_proto",
    ],
)
