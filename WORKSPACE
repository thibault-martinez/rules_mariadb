workspace(name = "rules_mariadb")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "mariadb",
    build_file = "//:BUILD",
    sha256 = "7afac2ef28aea7d71c95473c7a3da0f021a5ef2364480cd3e80eab83016341c2",
    strip_prefix = "mariadb-connector-c-3.1.3",
    url = "https://github.com/MariaDB/mariadb-connector-c/archive/v3.1.3.tar.gz",
)
