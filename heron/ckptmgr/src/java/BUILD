licenses(["notice"])

package(default_visibility = ["//visibility:public"])

java_library(
    name = "ckptmgr-java",
    srcs = glob(
        ["**/*.java"],
        exclude = ["**/CheckpointManager.java"],
    ),
    deps = [
        "//heron/spi/src/java:statefulstorage-spi-java",
        "//heron/common/src/java:basics-java",
        "//heron/common/src/java:config-java",
        "//heron/common/src/java:network-java",
        "//heron/common/src/java:utils-java",
        "//heron/proto:proto_common_java",
        "//heron/proto:proto_ckptmgr_java",
        "@com_google_protobuf//:protobuf_java",
    ],
)

java_binary(
    name = "ckptmgr-unshaded",
    srcs = glob(["**/CheckpointManager.java"]),
    deps = [
        ":ckptmgr-java",
        "//heron/spi/src/java:statefulstorage-spi-java",
        "//heron/api/src/java:api-java-low-level",
        "//heron/common/src/java:basics-java",
        "//heron/common/src/java:config-java",
        "//heron/common/src/java:network-java",
        "//heron/common/src/java:utils-java",
        "//heron/proto:proto_ckptmgr_java",
        "@commons_cli_commons_cli//jar",
    ],
)

jarjar_binary(
    name = "heron-ckptmgr",
    src = ":ckptmgr-unshaded_deploy.jar",
    shade = "shade.conf",
    deps = ["@org_sonatype_plugins_jarjar_maven_plugin//jar"]
)
