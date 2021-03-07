workspace(name = "com_github_ray_project_ray")

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "rules_proto",
    commit = "cfdc2fa31879c0aebe31ce7702b1a9c8a4be02d2",
    remote = "https://github.com/bazelbuild/rules_proto.git",
)

load("@rules_proto//proto:repositories.bzl", "rules_proto_dependencies", "rules_proto_toolchains")
rules_proto_dependencies()
rules_proto_toolchains()

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")
protobuf_deps()

load("//bazel:ray_deps_setup.bzl", "ray_deps_setup")

ray_deps_setup()

load("//bazel:ray_deps_build_all.bzl", "ray_deps_build_all")

ray_deps_build_all()

# This needs to be run after grpc_deps() in ray_deps_build_all() to make
# sure all the packages loaded by grpc_deps() are available. However a
# load() statement cannot be in a function so we put it here.
load("@com_github_grpc_grpc//bazel:grpc_extra_deps.bzl", "grpc_extra_deps")

grpc_extra_deps()
