workspace(name = "com_google_gold")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# abseil-cpp
http_archive(
  name = "com_google_absl",
	urls = ["http://gregcoppola.me/absl-cpp--sept-15-2019.zip"],
	sha256 = "bad7c7b472ea1e5b4dc48874097e493cf694965fc9ae11d1cf590825bc162cf1",
  strip_prefix = "abseil-cpp-master",
)

# Google Test
http_archive(
  name = "com_google_googletest",
  urls = ["https://github.com/google/googletest/archive/8b6d3f9c4a774bef3081195d422993323b6bb2e0.zip"],  # 2019-03-05
  strip_prefix = "googletest-8b6d3f9c4a774bef3081195d422993323b6bb2e0",
  sha256 = "d21ba93d7f193a9a0ab80b96e8890d520b25704a6fac976fe9da81fffb3392e3",
)

# C++ rules for Bazel.
http_archive(
    name = "rules_cc",
    sha256 = "67412176974bfce3f4cf8bdaff39784a72ed709fc58def599d1f68710b58d68b",
    strip_prefix = "rules_cc-b7fe9697c0c76ab2fd431a891dbb9a6a32ed7c3e",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_cc/archive/b7fe9697c0c76ab2fd431a891dbb9a6a32ed7c3e.zip",
        "https://github.com/bazelbuild/rules_cc/archive/b7fe9697c0c76ab2fd431a891dbb9a6a32ed7c3e.zip",
    ],
)
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "rules_python",
    remote = "https://github.com/bazelbuild/rules_python.git",
    # NOT VALID!  Replace this with a Git commit SHA.
    commit = "54d1cb35cd54318d59bf38e52df3e628c07d4bbc",
)

# This call should always be present.
load("@rules_python//python:repositories.bzl", "py_repositories")
py_repositories()

# This one is only needed if you're using the packaging rules.
load("@rules_python//python:pip.bzl", "pip_repositories")
pip_repositories()

http_archive(
    name = "rules_proto",
    sha256 = "602e7161d9195e50246177e7c55b2f39950a9cf7366f74ed5f22fd45750cd208",
    strip_prefix = "rules_proto-97d8af4dc474595af3900dd85cb3a29ad28cc313",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
        "https://github.com/bazelbuild/rules_proto/archive/97d8af4dc474595af3900dd85cb3a29ad28cc313.tar.gz",
    ],
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")
rules_proto_dependencies()
rules_proto_toolchains()

http_archive(
    name = "com_google_protobuf",
    strip_prefix = "protobuf-3.10.0-rc-1",
    sha256 = "edb05e4cf1364a9d149348b1a4aba4377185450e39693d930979c0efbed58fec",
    urls = [
        "https://github.com/protocolbuffers/protobuf/releases/download/v3.10.0-rc1/protobuf-all-3.10.0-rc-1.zip",
    ],
)

http_archive(
    name = "com_google_protobuf",
    strip_prefix = "protobuf-3.10.0-rc-1",
    sha256 = "edb05e4cf1364a9d149348b1a4aba4377185450e39693d930979c0efbed58fec",
    urls = [
        "https://github.com/protocolbuffers/protobuf/releases/download/v3.10.0-rc1/protobuf-all-3.10.0-rc-1.zip",
    ],
)


new_local_repository(
name = "libcurl",
path = "/usr/local",
build_file_content = """
cc_library(
name = "libcurl",
srcs = ["lib/libcurl.so"],
hdrs = glob(["include/**/*.h"]),
visibility = ["//visibility:public"]
)
"""
)
new_local_repository(
name = "libboost",
path = "/usr",
build_file_content = """
cc_library(
name = "libboost",
srcs = [
'lib/x86_64-linux-gnu/libboost_system.so',
'lib/x86_64-linux-gnu/libboost_filesystem.so',
'lib/x86_64-linux-gnu/libcrypto.so',
'lib/x86_64-linux-gnu/libssl.so',
'lib/x86_64-linux-gnu/libboost_stacktrace_addr2line.so',
'lib/x86_64-linux-gnu/libboost_stacktrace_backtrace.so',
'lib/x86_64-linux-gnu/libboost_stacktrace_basic.so',
'lib/x86_64-linux-gnu/libboost_stacktrace_noop.so',
],
hdrs = glob(["include/boost/**/*.h"]) + glob(["include/boost/**/*.hpp"]),
visibility = ["//visibility:public"]
)
"""
)

local_repository(
name = "hiredis",
path = __workspace_dir__ + "/../hiredis",
)

new_local_repository(
name = "libtorch",
path = __workspace_dir__ + "/../libtorch",
build_file_content = """
cc_library(
name = "libtorch",
srcs = glob(["lib/*.so" ]),
visibility = ["//visibility:public"],
)
"""
)
