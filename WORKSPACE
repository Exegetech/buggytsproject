workspace(name = "buggytsproject")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

##########
# skylib #
##########
http_archive(
    name = "bazel_skylib",
    sha256 = "b8a1527901774180afc798aeb28c4634bdccf19c4d98e7bdd1ce79d1fe9aaad7",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.4.1/bazel-skylib-1.4.1.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.4.1/bazel-skylib-1.4.1.tar.gz",
    ],
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

####################
# aspect bazel lib #
####################
http_archive(
    name = "aspect_bazel_lib",
    sha256 = "ee95bbc80f9ca219b93a8cc49fa19a2d4aa8649ddc9024f46abcdd33935753ca",
    strip_prefix = "bazel-lib-1.29.2",
    url = "https://github.com/aspect-build/bazel-lib/releases/download/v1.29.2/bazel-lib-v1.29.2.tar.gz",
)

load("@aspect_bazel_lib//lib:repositories.bzl", "aspect_bazel_lib_dependencies")

aspect_bazel_lib_dependencies()

########
# node #
########
http_archive(
    name = "build_bazel_rules_nodejs",
    sha256 = "94070eff79305be05b7699207fbac5d2608054dd53e6109f7d00d923919ff45a",
    url = "https://github.com/bazelbuild/rules_nodejs/releases/download/5.8.2/rules_nodejs-5.8.2.tar.gz",
)

http_archive(
    name = "rules_nodejs",
    sha256 = "764a3b3757bb8c3c6a02ba3344731a3d71e558220adcb0cf7e43c9bba2c37ba8",
    urls = ["https://github.com/bazelbuild/rules_nodejs/releases/download/5.8.2/rules_nodejs-core-5.8.2.tar.gz"],
)

load("@rules_nodejs//nodejs:repositories.bzl", "nodejs_register_toolchains")
load("@build_bazel_rules_nodejs//:repositories.bzl", "build_bazel_rules_nodejs_dependencies")
load("@build_bazel_rules_nodejs//:index.bzl", "node_repositories")

nodejs_register_toolchains(
    name = "node",
    node_version = "16.17.1",
)

node_repositories(
    node_version = "16.17.1"
)

######
# js #
######
http_archive(
    name = "aspect_rules_js",
    sha256 = "e3e6c3d42491e2938f4239a3d04259a58adc83e21e352346ad4ef62f87e76125",
    strip_prefix = "rules_js-1.30.0",
    url = "https://github.com/aspect-build/rules_js/releases/download/v1.30.0/rules_js-v1.30.0.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

###########
# pnpm #
##########
load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    data = [
        "//:package.json",
        "//:pnpm-workspace.yaml",
        "//:mypackage/package.json",
    ],
    npmrc = "//:.npmrc",
    pnpm_lock = "//:pnpm-lock.yaml",
    pnpm_version = "8.6.0",
    quiet = False,
    verify_node_modules_ignored = "//:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()

#######
# swc #
#######
http_archive(
    name = "aspect_rules_swc",
    sha256 = "6ee206f7aa7f6aa75e7c3dbfc9b66c2e759851e49690b26154c86465d4e7f859",
    strip_prefix = "rules_swc-1.0.0",
    url = "https://github.com/aspect-build/rules_swc/releases/download/v1.0.0/rules_swc-v1.0.0.tar.gz",
)

load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")

rules_swc_dependencies()

load("@aspect_rules_swc//swc:repositories.bzl", "LATEST_VERSION", "swc_register_toolchains")

swc_register_toolchains(
    name = "swc",
    swc_version = LATEST_VERSION,
)

#######
# ts #
#######
http_archive(
    name = "aspect_rules_ts",
    sha256 = "58b6c0ad158fc42883dafa157f1a25cddd65bcd788a772620192ac9ceefa0d78",
    strip_prefix = "rules_ts-1.3.2",
    url = "https://github.com/aspect-build/rules_ts/releases/download/v1.3.2/rules_ts-v1.3.2.tar.gz",
)

load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies")

rules_ts_dependencies(
    ts_version_from = "//:package.json",
)

###########
# esbuild #
##########
http_archive(
    name = "aspect_rules_esbuild",
    sha256 = "2ea31bd97181a315e048be693ddc2815fddda0f3a12ca7b7cc6e91e80f31bac7",
    strip_prefix = "rules_esbuild-0.14.4",
    url = "https://github.com/aspect-build/rules_esbuild/releases/download/v0.14.4/rules_esbuild-v0.14.4.tar.gz",
)

load("@aspect_rules_esbuild//esbuild:dependencies.bzl", "rules_esbuild_dependencies")

rules_esbuild_dependencies()

load("@aspect_rules_esbuild//esbuild:repositories.bzl", "LATEST_VERSION", "esbuild_register_toolchains")

esbuild_register_toolchains(
    name = "esbuild",
    esbuild_version = LATEST_VERSION,
)

