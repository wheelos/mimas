load("@rules_cc//cc:defs.bzl", "cc_library", "cc_test")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "math",
    deps = [
        ":angle",
        ":cartesian_frenet_conversion",
        ":curve_fitting",
        ":euler_angles_zxy",
        ":factorial",
        ":geometry",
        ":integral",
        ":kalman_filter",
        ":linear_interpolation",
        ":lqr",
        ":quaternion",
        ":search",
        ":sin_table",
    ],
)

cc_library(
    name = "math_utils",
    srcs = ["math_utils.cc"],
    hdrs = ["math_utils.h"],
    linkopts = ["-lm"],
    deps = [
        ":vec2d",
        "@eigen",
    ],
)

cc_library(
    name = "vec2d",
    srcs = ["vec2d.cc"],
    hdrs = ["vec2d.h"],
    linkopts = ["-lm"],
    deps = [
        "@wheel_core//cyber/common:log",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "geometry",
    srcs = [
        "aabox2d.cc",
        "box2d.cc",
        "line_segment2d.cc",
        "polygon2d.cc",
    ],
    hdrs = [
        "aabox2d.h",
        "aaboxkdtree2d.h",
        "box2d.h",
        "line_segment2d.h",
        "polygon2d.h",
    ],
    linkopts = ["-lm"],
    deps = [
        ":math_utils",
        "@wheel_core//cyber/common:log",
        "//util:string_util",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "sin_table",
    srcs = ["sin_table.cc"],
    hdrs = ["sin_table.h"],
)

cc_library(
    name = "angle",
    srcs = ["angle.cc"],
    hdrs = ["angle.h"],
    deps = [
        ":sin_table",
    ],
)

cc_library(
    name = "euler_angles_zxy",
    hdrs = ["euler_angles_zxy.h"],
    deps = [
        ":geometry",
        "@eigen",
    ],
)

cc_library(
    name = "quaternion",
    hdrs = ["quaternion.h"],
    deps = [
        ":euler_angles_zxy",
        ":geometry",
        "@wheelos_common_msgs//common_msgs/basic_msgs:geometry_cc_proto",
        "@eigen",
    ],
)

cc_library(
    name = "curve_fitting",
    hdrs = ["curve_fitting.h"],
    deps = [
        ":matrix_operations",
        "@eigen",
    ],
)

cc_library(
    name = "matrix_operations",
    srcs = ["matrix_operations.cc"],
    hdrs = ["matrix_operations.h"],
    deps = [
        "@wheel_core//cyber/common:log",
        "@eigen",
    ],
)

cc_test(
    name = "matrix_operations_test",
    size = "small",
    srcs = ["matrix_operations_test.cc"],
    linkopts = ["-lm"],
    deps = [
        ":matrix_operations",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_library(
    name = "kalman_filter",
    hdrs = ["kalman_filter.h"],
    deps = [
        "@wheel_core//cyber/common:log",
        ":matrix_operations",
        "@eigen",
    ],
)

cc_library(
    name = "factorial",
    hdrs = ["factorial.h"],
)

cc_library(
    name = "path_matcher",
    srcs = ["path_matcher.cc"],
    hdrs = ["path_matcher.h"],
    deps = [
        ":linear_interpolation",
        "@wheelos_common_msgs//common_msgs/basic_msgs:pnc_point_cc_proto",
    ],
)

cc_test(
    name = "angle_test",
    size = "small",
    srcs = ["angle_test.cc"],
    linkopts = [
        "-lm",
    ],
    deps = [
        ":angle",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_library(
    name = "search",
    srcs = ["search.cc"],
    hdrs = ["search.h"],
)

cc_library(
    name = "linear_interpolation",
    srcs = ["linear_interpolation.cc"],
    hdrs = ["linear_interpolation.h"],
    deps = [
        ":geometry",
        "@wheelos_common_msgs//common_msgs/basic_msgs:pnc_point_cc_proto",
    ],
)

cc_library(
    name = "integral",
    srcs = ["integral.cc"],
    hdrs = ["integral.h"],
    deps = [
        "@wheel_core//cyber/common:log",
    ],
)

cc_library(
    name = "lqr",
    srcs = ["linear_quadratic_regulator.cc"],
    hdrs = ["linear_quadratic_regulator.h"],
    deps = [
        "@wheel_core//cyber/common:log",
        "@eigen",
    ],
)

cc_library(
    name = "cartesian_frenet_conversion",
    srcs = ["cartesian_frenet_conversion.cc"],
    hdrs = ["cartesian_frenet_conversion.h"],
    deps = [
        ":geometry",
        "@wheel_core//cyber/common:log",
        "@eigen",
    ],
)

cc_library(
    name = "hermite_spline",
    hdrs = ["hermite_spline.h"],
    deps = [
        "@wheel_core//cyber/common:log",
    ],
)

cc_test(
    name = "math_utils_test",
    size = "small",
    srcs = ["math_utils_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "linear_interpolation_test",
    size = "small",
    srcs = ["linear_interpolation_test.cc"],
    deps = [
        ":linear_interpolation",
        "@wheel_core//cyber/common:log",
        "@com_google_googletest//:gtest_main",
        "@eigen",
    ],
)

cc_test(
    name = "search_test",
    size = "small",
    srcs = ["search_test.cc"],
    linkopts = [
        "-lm",
    ],
    deps = [
        ":search",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "integral_test",
    size = "small",
    srcs = ["integral_test.cc"],
    linkopts = [
        "-lm",
    ],
    deps = [
        ":integral",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "vec2d_test",
    size = "small",
    srcs = ["vec2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "quaternion_test",
    size = "small",
    srcs = ["quaternion_test.cc"],
    deps = [
        ":quaternion",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "euler_angles_zxy_test",
    size = "small",
    srcs = ["euler_angles_zxy_test.cc"],
    deps = [
        ":euler_angles_zxy",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "aabox2d_test",
    size = "small",
    srcs = ["aabox2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "aaboxkdtree2d_test",
    size = "small",
    srcs = ["aaboxkdtree2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "box2d_test",
    size = "small",
    srcs = ["box2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "polygon2d_test",
    size = "small",
    srcs = ["polygon2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "line_segment2d_test",
    size = "small",
    srcs = ["line_segment2d_test.cc"],
    deps = [
        ":geometry",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "kalman_filter_test",
    size = "small",
    srcs = ["kalman_filter_test.cc"],
    linkopts = ["-lm"],
    deps = [
        ":kalman_filter",
        "@com_google_googletest//:gtest_main",
    ],
)

cc_test(
    name = "cartesian_frenet_conversion_test",
    size = "small",
    srcs = ["cartesian_frenet_conversion_test.cc"],
    deps = [
        ":cartesian_frenet_conversion",
        "@com_google_googletest//:gtest_main",
    ],
)
