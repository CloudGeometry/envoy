load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_extension",
    "envoy_cc_library",
    "envoy_extension_package",
)

licenses(["notice"])  # Apache 2

envoy_extension_package()

envoy_cc_library(
    name = "profile_action_lib",
    srcs = ["profile_action.cc"],
    hdrs = ["profile_action.h"],
    deps = [
        "//envoy/api:api_interface",
        "//envoy/common:time_interface",
        "//envoy/event:timer_interface",
        "//envoy/server:guarddog_config_interface",
        "//envoy/thread:thread_interface",
        "//source/common/profiler:profiler_lib",
        "//source/common/protobuf:utility_lib",
        "//source/common/stats:symbol_table_lib",
        "@com_google_absl//absl/types:optional",
        "@envoy_api//envoy/extensions/watchdog/profile_action/v3:pkg_cc_proto",
    ],
)

envoy_cc_extension(
    name = "config",
    srcs = ["config.cc"],
    hdrs = ["config.h"],
    deps = [
        ":profile_action_lib",
        "//envoy/registry",
        "//source/common/common:assert_lib",
        "//source/common/config:utility_lib",
        "//source/common/protobuf",
        "//source/common/protobuf:message_validator_lib",
        "@envoy_api//envoy/extensions/watchdog/profile_action/v3:pkg_cc_proto",
    ],
)
