licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_package",
)

envoy_package()

envoy_cc_library(
    name = "ext_authz_interface",
    hdrs = ["ext_authz.h"],
    deps = [
        "//include/envoy/http:codes_interface",
        "//source/common/tracing:http_tracer_lib",
        "@envoy_api//envoy/service/auth/v2alpha:external_auth_cc",
    ],
)

envoy_cc_library(
    name = "ext_authz_grpc_lib",
    srcs = ["ext_authz_grpc_impl.cc"],
    hdrs = ["ext_authz_grpc_impl.h"],
    deps = [
        ":check_request_utils_lib",
        ":ext_authz_interface",
        "//include/envoy/grpc:async_client_interface",
        "//include/envoy/grpc:async_client_manager_interface",
        "//include/envoy/http:filter_interface",
        "//include/envoy/http:header_map_interface",
        "//include/envoy/http:protocol_interface",
        "//include/envoy/network:address_interface",
        "//include/envoy/network:connection_interface",
        "//include/envoy/network:filter_interface",
        "//include/envoy/upstream:cluster_manager_interface",
        "//source/common/common:assert_lib",
        "//source/common/grpc:async_client_lib",
        "//source/common/http:headers_lib",
        "//source/common/http:utility_lib",
        "//source/common/network:utility_lib",
        "//source/common/protobuf",
        "//source/common/tracing:http_tracer_lib",
    ],
)

envoy_cc_library(
    name = "ext_authz_http_lib",
    srcs = ["ext_authz_http_impl.cc"],
    hdrs = ["ext_authz_http_impl.h"],
    deps = [
        ":check_request_utils_lib",
        ":ext_authz_interface",
        "//include/envoy/upstream:cluster_manager_interface",
        "//source/common/common:matchers_lib",
        "//source/common/common:minimal_logger_lib",
        "//source/common/http:async_client_lib",
        "//source/common/http:codes_lib",
        "@envoy_api//envoy/config/filter/http/ext_authz/v2alpha:ext_authz_cc",
    ],
)

envoy_cc_library(
    name = "check_request_utils_lib",
    srcs = ["check_request_utils.cc"],
    hdrs = ["check_request_utils.h"],
    deps = [
        "//include/envoy/grpc:async_client_interface",
        "//include/envoy/grpc:async_client_manager_interface",
        "//include/envoy/http:filter_interface",
        "//include/envoy/upstream:cluster_manager_interface",
        "//source/common/grpc:async_client_lib",
        "@envoy_api//envoy/service/auth/v2alpha:external_auth_cc",
    ],
)
