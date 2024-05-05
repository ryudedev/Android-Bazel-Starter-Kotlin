load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

android_sdk_repository(
    name = "androidsdk",
    api_level = 34,
    build_tools_version = "34.0.0",
    path="/Users/it/Library/Android/sdk"
)

http_archive(
    name = "rules_android",
    urls = ["https://github.com/bazelbuild/rules_android/archive/v0.1.1.zip"],
    sha256 = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806",
    strip_prefix = "rules_android-0.1.1",
)

RULES_JVM_EXTERNAL_TAG = "4.5"
RULES_JVM_EXTERNAL_SHA = "b17d7388feb9bfa7f2fa09031b32707df529f26c91ab9e5d909eb1676badd9a6"

http_archive(
    name = "rules_jvm_external",
    strip_prefix = "rules_jvm_external-%s" % RULES_JVM_EXTERNAL_TAG,
    sha256 = RULES_JVM_EXTERNAL_SHA,
    url = "https://github.com/bazelbuild/rules_jvm_external/archive/%s.zip" % RULES_JVM_EXTERNAL_TAG,
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "androidx.appcompat:appcompat:1.0.2",
        "androidx.fragment:fragment:1.0.0",
        "androidx.core:core:1.0.1",
        "androidx.lifecycle:lifecycle-runtime:2.0.0",
        "androidx.lifecycle:lifecycle-viewmodel:2.0.0",
        "androidx.lifecycle:lifecycle-common:2.0.0",
        "androidx.drawerlayout:drawerlayout:1.0.0",
        "androidx.constraintlayout:constraintlayout:1.1.3",
        "com.google.android.material:material:1.0.0",
        "org.jetbrains.kotlinx:kotlinx-coroutines-core:1.3.2",
        "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.2"
    ],
    repositories = [
        "https://maven.google.com",
        "https://jcenter.bintray.com",
    ],
    fetch_sources = True,
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

kotlin_version = "1.3.61"
kotlin_release_sha = "3901151ad5d94798a268d1771c6c0b7e305a608c2889fc98a674802500597b1c"
rules_kotlin_compiler_release = {
    "urls": [
    "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = kotlin_version),
    ],
    "sha256": kotlin_release_sha,
}

rules_kotlin_version = "1.8.1"
rules_kotlin_sha = "a630cda9fdb4f56cf2dc20a4bf873765c41cf00e9379e8d59cd07b24730f4fde"
http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = rules_kotlin_sha,
    urls = ["https://github.com/bazelbuild/rules_kotlin/releases/download/v%s/rules_kotlin_release.tgz" % rules_kotlin_version],
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories", "kt_register_toolchains")
kotlin_repositories(compiler_release = rules_kotlin_compiler_release)
kt_register_toolchains()
