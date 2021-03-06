load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "discretized_trajectory",
    srcs = [
        "discretized_trajectory.cc",
    ],
    hdrs = [
        "discretized_trajectory.h",
    ],
    deps = [
        "//modules/common/math:linear_interpolation",
        "//modules/common/proto:pnc_point_proto",
        "//modules/common/vehicle_state/proto:vehicle_state_proto",
        "//modules/planning/common:planning_context",
        "@eigen",
    ],
)

cc_test(
    name = "discretized_trajectory_test",
    size = "small",
    srcs = [
        "discretized_trajectory_test.cc",
    ],
    data = [
        "//modules/planning:planning_testdata",
    ],
    deps = [
        ":discretized_trajectory",
        "//modules/common/util",
        "@gtest//:main",
    ],
)

cc_library(
    name = "publishable_trajectory",
    srcs = [
        "publishable_trajectory.cc",
    ],
    hdrs = [
        "publishable_trajectory.h",
    ],
    deps = [
        ":discretized_trajectory",
        "//modules/planning/proto:planning_proto",
    ],
)

cc_test(
    name = "publishable_trajectory_test",
    size = "small",
    srcs = [
        "publishable_trajectory_test.cc",
    ],
    data = [
        "//modules/planning:planning_testdata",
    ],
    deps = [
        ":publishable_trajectory",
        "//modules/common/util",
        "@gtest//:main",
    ],
)

cc_library(
    name = "trajectory_stitcher",
    srcs = [
        "trajectory_stitcher.cc",
    ],
    hdrs = [
        "trajectory_stitcher.h",
    ],
    deps = [
        ":publishable_trajectory",
        "//cyber/common:log",
        "//modules/common/proto:pnc_point_proto",
        "//modules/planning/common:planning_gflags",
        "//modules/planning/reference_line",
    ],
)

cpplint()
