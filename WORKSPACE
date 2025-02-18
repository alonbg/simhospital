load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "io_bazel_rules_go",
    sha256 = "8e968b5fcea1d2d64071872b12737bbb5514524ee5f0a4f54f5920266c261acb",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/rules_go/releases/download/v0.28.0/rules_go-v0.28.0.zip",
        "https://github.com/bazelbuild/rules_go/releases/download/v0.28.0/rules_go-v0.28.0.zip",
    ],
)

http_archive(
    name = "bazel_gazelle",
    sha256 = "62ca106be173579c0a167deb23358fdfe71ffa1e4cfdddf5582af26520f1c66f",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-gazelle/releases/download/v0.23.0/bazel-gazelle-v0.23.0.tar.gz",
        "https://github.com/bazelbuild/bazel-gazelle/releases/download/v0.23.0/bazel-gazelle-v0.23.0.tar.gz",
    ],
)

http_archive(
    name = "com_google_protobuf",
    sha256 = "d0f5f605d0d656007ce6c8b5a82df3037e1d8fe8b121ed42e536f569dec16113",
    strip_prefix = "protobuf-3.14.0",
    urls = [
        "https://mirror.bazel.build/github.com/protocolbuffers/protobuf/archive/v3.14.0.tar.gz",
        "https://github.com/protocolbuffers/protobuf/archive/v3.14.0.tar.gz",
    ],
)

http_archive(
    name = "io_bazel_rules_docker",
    sha256 = "1f4e59843b61981a96835dc4ac377ad4da9f8c334ebe5e0bb3f58f80c09735f4",
    strip_prefix = "rules_docker-0.19.0",
    urls = ["https://github.com/bazelbuild/rules_docker/releases/download/v0.19.0/rules_docker-v0.19.0.tar.gz"],
)

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies")
load("//:repositories.bzl", "go_repositories")

# gazelle:repository_macro repositories.bzl%go_repositories
go_repositories()

go_register_toolchains(version = "1.17")

gazelle_dependencies()

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()

load(
    "@io_bazel_rules_docker//repositories:repositories.bzl",
    container_repositories = "repositories",
)

container_repositories()

load("@io_bazel_rules_docker//repositories:deps.bzl", container_deps = "deps")

container_deps()

# load("@io_bazel_rules_docker//repositories:pip_repositories.bzl", "pip_deps")

# pip_deps()

# See: https://github.com/bazelbuild/rules_docker#go_image

load(
    "@io_bazel_rules_docker//go:image.bzl",
    _go_image_repos = "repositories",
)

_go_image_repos()

load("@io_bazel_rules_docker//container:container.bzl", "container_pull")

container_pull(
    name = "ubuntu",
    digest = "sha256:c81e8f6bcbab8818fdbe2df6d367990ab55d85b4dab300931a53ba5d082f4296",
    registry = "gcr.io",
    repository = "cloud-marketplace-containers/google/ubuntu16_04",
)

# go_repository(
#     name = "com_github_sirupsen_logrus",
#     importpath = "github.com/sirupsen/logrus",
#     sum = "h1:dJKuHgqk1NNQlqoA6BTlM1Wf9DOH3NBjQyu0h9+AZZE=",
#     version = "v1.8.1",
# )

# go_repository(
#     name = "com_github_pkg_errors",
#     importpath = "github.com/pkg/errors",
#     sum = "h1:FEBLx1zS214owpjy7qsBeixbURkuhQAwrK5UwLGTwt4=",
#     version = "v0.9.1",
# )

# go_repository(
#     name = "in_gopkg_yaml_v2",
#     importpath = "gopkg.in/yaml.v2",
#     sum = "h1:obN1ZagJSUGI0Ek/LBmuj4SNLPfIny3KsKFopxRdj10=",
#     version = "v2.2.8",
# )

# go_repository(
#     name = "com_github_google_go_cmp",
#     importpath = "github.com/google/go-cmp",
#     sum = "h1:xsAVV57WRhGj6kEIi8ReJzQlHHqcBYCElAvkovg3B/4=",
#     version = "v0.4.0",
# )

# go_repository(
#     name = "com_github_gorilla_mux",
#     importpath = "github.com/gorilla/mux",
#     sum = "h1:VuZ8uybHlWmqV03+zRzdwKL4tUnIp1MAQtp1mIFE1bc=",
#     version = "v1.7.4",
# )

# go_repository(
#     name = "com_github_prometheus_client_model",
#     importpath = "github.com/prometheus/client_model",
#     sum = "h1:uq5h0d+GuxiXLJLNABMgp2qUWDPiLvgCzz2dUR+/W/M=",
#     version = "v0.2.0",
# )

# go_repository(
#     name = "com_github_golang_collections_go_datastructures",
#     importpath = "github.com/golang-collections/go-datastructures",
#     sum = "h1:ZHJ7+IGpuOXtVf6Zk/a3WuHQgkC+vXwaqfUBDFwahtI=",
#     version = "v0.0.0-20150211160725-59788d5eb259",
# )

# go_repository(
#     name = "org_golang_x_text",
#     importpath = "golang.org/x/text",
#     sum = "h1:tW2bmiBqwgJj/UpqtC8EpXEZVYOwU0yG4iWbprSVAcs=",
#     version = "v0.3.2",
# )

# go_repository(
#     name = "org_golang_x_net",
#     importpath = "golang.org/x/net",
#     sum = "h1:GuSPYbZzB5/dcLNCwLQLsg3obCJtX9IJhpXkvY7kzk0=",
#     version = "v0.0.0-20200301022130-244492dfa37a",
# )

# go_repository(
#     name = "com_github_golang_protobuf",
#     importpath = "github.com/golang/protobuf",
#     sum = "h1:+Z5KGCizgyZCbGh1KZqA0fcLLkwbsjIzS4aV2v7wJX0=",
#     version = "v1.4.2",
# )

# go_repository(
#     name = "com_github_prometheus_procfs",
#     build_file_proto_mode = "disable",
#     commit = "6d489fc7f1d9cd890a250f3ea3431b1744b9623f",
#     importpath = "github.com/prometheus/procfs",
# )

# go_repository(
#     name = "org_golang_x_sync",
#     importpath = "golang.org/x/sync",
#     sum = "h1:vcxGaoTs7kV8m5Np9uUNQin4BrLOthgV7252N8V+FwY=",
#     version = "v0.0.0-20190911185100-cd5d95a43a6e",
# )

# go_repository(
#     name = "com_github_prometheus_client_golang",
#     build_file_proto_mode = "disable",
#     commit = "170205fb58decfd011f1550d4cfb737230d7ae4f",
#     importpath = "github.com/prometheus/client_golang",
# )

# go_repository(
#     name = "com_github_beorn7_perks",
#     build_file_proto_mode = "disable",
#     commit = "37c8de3658fcb183f997c4e13e8337516ab753e6",
#     importpath = "github.com/beorn7/perks",
# )

# go_repository(
#     name = "com_github_prometheus_common",
#     commit = "7600349dcfe1abd18d72d3a1770870d9800a7801",
#     importpath = "github.com/prometheus/common",
# )

# go_repository(
#     name = "org_golang_x_xerrors",
#     importpath = "golang.org/x/xerrors",
#     sum = "h1:E7g+9GITq07hpfrRu66IVDexMakfv52eLZ2CXBWiKr4=",
#     version = "v0.0.0-20191204190536-9bdfabe68543",
# )

# go_repository(
#     name = "com_github_google_uuid",
#     importpath = "github.com/google/uuid",
#     sum = "h1:Gkbcsh/GbpXz7lPftLA3P6TYMwjCLYm83jiFQZF/3gY=",
#     version = "v1.1.1",
# )

# go_repository(
#     name = "org_golang_x_crypto",
#     importpath = "golang.org/x/crypto",
#     sum = "h1:9bFeDpN3gTqNanMVqNcoR/pJQuP5uroC3t1D7eXozTE=",
#     version = "v0.0.0-20191119213627-4f8c1d86b1ba",
# )

# go_repository(
#     name = "com_github_matttproud_golang_protobuf_extensions",
#     build_file_proto_mode = "disable",
#     commit = "c12348ce28de40eed0136aa2b644d0ee0650e56c",
#     importpath = "github.com/matttproud/golang_protobuf_extensions",
# )

load("@com_google_fhir//bazel:go_dependencies.bzl", "fhir_go_dependencies")

fhir_go_dependencies()

# go_repository(
#     name = "org_golang_google_protobuf",
#     importpath = "google.golang.org/protobuf",
#     sum = "h1:Ejskq+SyPohKW+1uil0JJMtmHCgJPJ/qWTxr8qp+R4c=123",
#     version = "v1.25.0",
# )

# go_repository(
#     name = "com_google_cloud_go",
#     importpath = "cloud.google.com/go",
#     sum = "h1:BM3svUDU3itpc2m5cu5wCyThIYNDlFlts9GASw31GW8=",
#     version = "v0.59.0",
# )

# go_repository(
#     name = "org_golang_google_api",
#     importpath = "google.golang.org/api",
#     sum = "h1:jMF5hhVfMkTZwHW1SDpKq5CkgWLXOb31Foaca9Zr3oM=",
#     version = "v0.28.0",
# )

# go_repository(
#     name = "com_google_cloud_go_storage",
#     importpath = "cloud.google.com/go/storage",
#     sum = "h1:STgFzyU5/8miMl0//zKh2aQeTyeaUH3WN9bSUiJ09bA=",
#     version = "v1.10.0",
# )

# go_repository(
#     name = "com_github_googleapis_gax_go",
#     importpath = "github.com/googleapis/gax-go",
#     sum = "h1:9dMLqhaibYONnDRcnHdUs9P8Mw64jLlZTYlDe3leBtQ=",
#     version = "v1.0.3",
# )

# go_repository(
#     name = "com_github_googleapis_gax_go_v2",
#     importpath = "github.com/googleapis/gax-go/v2",
#     sum = "h1:sjZBwGj9Jlw33ImPtvFviGYvseOtDM7hkSKB7+Tv3SM=",
#     version = "v2.0.5",
# )

# go_repository(
#     name = "org_golang_google_grpc",
#     importpath = "google.golang.org/grpc",
#     sum = "h1:M5a8xTlYTxwMn5ZFkwhRabsygDY5G8TYLyQDBxJNAxE=",
#     version = "v1.30.0",
# )

# go_repository(
#     name = "io_opencensus_go",
#     importpath = "go.opencensus.io",
#     sum = "h1:LYy1Hy3MJdrCdMwwzxA/dRok4ejH+RwNGbuoD9fCjto=",
#     version = "v0.22.4",
# )

# go_repository(
#     name = "org_golang_x_oauth2",
#     importpath = "golang.org/x/oauth2",
#     sum = "h1:TzXSXBo42m9gQenoE3b9BGiEpg5IG2JkU5FkPIawgtw=",
#     version = "v0.0.0-20200107190931-bf48bf16ab8d",
# )

# go_repository(
#     name = "com_github_golang_groupcache",
#     importpath = "github.com/golang/groupcache",
#     sum = "h1:1r7pUrabqp18hOBcwBwiTsbnFeTZHV9eER/QT5JVZxY=",
#     version = "v0.0.0-20200121045136-8c9f03a8e57e",
# )
