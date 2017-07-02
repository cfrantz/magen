package(default_visibility = ["//visibility:public"])
load("@mxebzl//tools/windows:rules.bzl", "pkg_winzip")

config_setting(
    name = "windows",
    values = {
        "crosstool_top": "@mxebzl//tools/windows:toolchain",
    }
)

cc_binary(
    name = "magen",
    data = ["//content"],
    linkopts = select({
        ":windows": ["-mwindows"],
        "//conditions:default": [],
    }) + [
        "-lSDL2",
        "-lSDL2main",
        "-lSDL2_mixer",
    ],
    srcs = ["main.cc"],
    deps = [
        ":music_screen",
        "@libgam//:game",
    ],
)

pkg_winzip(
    name = "magen-windows",
    files = [
        ":magen",
        "//content",
    ],
)

cc_library(
    name = "music_generator",
    srcs = ["music_generator.cc"],
    hdrs = ["music_generator.h"],
)

cc_library(
    name = "music_screen",
    srcs = ["music_screen.cc"],
    hdrs = ["music_screen.h"],
    deps = [
        ":music_generator",
        "@libgam//:screen",
        "@libgam//:text",
    ],
)
