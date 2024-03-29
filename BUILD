genrule(
    name = "mariadb_version_h",
    outs = ["include/mariadb_version.h"],
    cmd = select({
        "@bazel_tools//src/conditions:darwin": """cat > $@ <<"EOF"
/* Copyright Abandoned 1996, 1999, 2001 MySQL AB
   This file is public domain and comes with NO WARRANTY of any kind */

/* Version numbers for protocol & mysqld */

#ifndef _mariadb_version_h_
#define _mariadb_version_h_

#ifdef _CUSTOMCONFIG_
#include <custom_conf.h>
#else
#define PROTOCOL_VERSION		10
#define MARIADB_CLIENT_VERSION_STR	"10.4.3"
#define MARIADB_BASE_VERSION		"mariadb-10.4"
#define MARIADB_VERSION_ID		100403
#define MARIADB_PORT	        	3306
#define MARIADB_UNIX_ADDR               "/tmp/mysql.sock"

#define MYSQL_CONFIG_NAME               "my"
#define MYSQL_VERSION_ID                100403
#define MYSQL_SERVER_VERSION            "10.4.3-MariaDB"

#define MARIADB_PACKAGE_VERSION "3.1.4"
#define MARIADB_PACKAGE_VERSION_ID 30104
#define MARIADB_SYSTEM_TYPE "Darwin"
#define MARIADB_MACHINE_TYPE "x86_64"
#define MARIADB_PLUGINDIR "/usr/local//usr/local/lib/mariadb/plugin"

/* mysqld compile time options */
#ifndef MYSQL_CHARSET
#define MYSQL_CHARSET			""
#endif
#endif

/* Source information */
#define CC_SOURCE_REVISION "4dc2ed0b9b563911fe519222c4a758966b445278"

#endif /* _mariadb_version_h_ */
EOF""",
        "@bazel_tools//src/conditions:windows": """cat > $@ <<"EOF"
EOF""",
        "//conditions:default": """cat > $@ <<"EOF"
EOF""",
    }),
)

genrule(
    name = "ma_config_h",
    outs = ["include/ma_config.h"],
    cmd = select({
        "@bazel_tools//src/conditions:darwin": """cat > $@ <<"EOF"
/*
 * Include file constants (processed in LibmysqlIncludeFiles.txt 1
 */
/* #undef HAVE_OPENSSL_APPLINK_C */
#define HAVE_ALLOCA_H 1
/* #undef HAVE_BIGENDIAN */
#define HAVE_SETLOCALE 1
#define HAVE_NL_LANGINFO 1
#define HAVE_DLFCN_H 1
#define HAVE_FCNTL_H 1
#define HAVE_FLOAT_H 1
#define HAVE_LIMITS_H 1
#define HAVE_PWD_H 1
/* #undef HAVE_SELECT_H */
#define HAVE_STDDEF_H 1
#define HAVE_STDINT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_SYS_IOCTL_H 1
#define HAVE_SYS_SELECT_H 1
#define HAVE_SYS_SOCKET_H 1
/* #undef HAVE_SYS_STREAM_H */
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_UN_H 1
#define HAVE_UNISTD_H 1
/* #undef HAVE_UCONTEXT_H */

/*
 * function definitions - processed in LibmysqlFunctions.txt
 */

#define HAVE_DLERROR 1
#define HAVE_DLOPEN 1
/* #undef HAVE_GETPWUID */
#define HAVE_MEMCPY 1
#define HAVE_POLL 1
/* #undef HAVE_STRTOK_R */
/* #undef HAVE_STRTOL */
/* #undef HAVE_STRTOLL */
/* #undef HAVE_STRTOUL */
/* #undef HAVE_STRTOULL */
/* #undef HAVE_TELL */
/* #undef HAVE_THR_SETCONCURRENCY */
/* #undef HAVE_THR_YIELD */
/* #undef HAVE_VASPRINTF */
/* #undef HAVE_VSNPRINTF */

/*
 * types and sizes
 */


#define SIZEOF_CHARP 8
#if defined(SIZEOF_CHARP)
# define HAVE_CHARP 1
#endif


#define SIZEOF_INT 4
#if defined(SIZEOF_INT)
# define HAVE_INT 1
#endif

#define SIZEOF_LONG 8
#if defined(SIZEOF_LONG)
# define HAVE_LONG 1
#endif

#define SIZEOF_LONG_LONG 8
#if defined(SIZEOF_LONG_LONG)
# define HAVE_LONG_LONG 1
#endif


#define SIZEOF_SIZE_T 8
#if defined(SIZEOF_SIZE_T)
# define HAVE_SIZE_T 1
#endif


#define SIZEOF_UINT 4
#if defined(SIZEOF_UINT)
# define HAVE_UINT 1
#endif

/* #undef SIZEOF_ULONG */
#if defined(SIZEOF_ULONG)
# define HAVE_ULONG 1
#endif

/* #undef SIZEOF_INT8 */
#if defined(SIZEOF_INT8)
# define HAVE_INT8 1
#endif
/* #undef SIZEOF_UINT8 */
#if defined(SIZEOF_UINT8)
# define HAVE_UINT8 1
#endif

/* #undef SIZEOF_INT16 */
#if defined(SIZEOF_INT16)
# define HAVE_INT16 1
#endif
/* #undef SIZEOF_UINT16 */
#if defined(SIZEOF_UINT16)
# define HAVE_UINT16 1
#endif

/* #undef SIZEOF_INT32 */
#if defined(SIZEOF_INT32)
# define HAVE_INT32 1
#endif
/* #undef SIZEOF_UINT32 */
#if defined(SIZEOF_UINT32)
# define HAVE_UINT32 1
#endif

/* #undef SIZEOF_INT64 */
#if defined(SIZEOF_INT64)
# define HAVE_INT64 1
#endif
/* #undef SIZEOF_UINT64 */
#if defined(SIZEOF_UINT64)
# define HAVE_UINT64 1
#endif

/* #undef SIZEOF_SOCKLEN_T */
#if defined(SIZEOF_SOCKLEN_T)
# define HAVE_SOCKLEN_T 1
#endif

#define SOCKET_SIZE_TYPE socklen_t

#define LOCAL_INFILE_MODE_OFF  0
#define LOCAL_INFILE_MODE_ON   1
#define LOCAL_INFILE_MODE_AUTO 2
#define ENABLED_LOCAL_INFILE LOCAL_INFILE_MODE_AUTO

#define MARIADB_DEFAULT_CHARSET "latin1"
EOF""",
        "@bazel_tools//src/conditions:windows": """cat > $@ <<"EOF"
EOF""",
        "//conditions:default": """cat > $@ <<"EOF"
EOF""",
    }),
)

cc_library(
    name = "zlib",
    srcs = [
        "zlib/adler32.c",
        "zlib/compress.c",
        "zlib/crc32.c",
        "zlib/deflate.c",
        "zlib/gzclose.c",
        "zlib/gzlib.c",
        "zlib/gzread.c",
        "zlib/gzwrite.c",
        "zlib/infback.c",
        "zlib/inffast.c",
        "zlib/inflate.c",
        "zlib/inftrees.c",
        "zlib/minigzip.c",
        "zlib/trees.c",
        "zlib/uncompr.c",
        "zlib/zutil.c",
    ],
    hdrs = glob(["zlib/*.h"]),
    visibility = ["//visibility:private"],
)

cc_library(
    name = "mariadb-hdrs",
    hdrs = glob(["include/**/*.h"]) + [
        ":ma_config_h",
        ":mariadb_version_h",
    ],
    strip_include_prefix = "include",
)

cc_library(
    name = "mariadb-plugin-auth",
    srcs = [
        "libmariadb/get_password.c",
        "plugins/auth/dialog.c",
        "plugins/auth/my_auth.c",
        "plugins/auth/old_password.c",
    ],
    hdrs = glob([
        "plugins/auth/**/*.h",
    ]),
    visibility = ["//visibility:private"],
    deps = [":mariadb-hdrs"],
)

cc_library(
    name = "mariadb-plugin-pvio",
    srcs = [
        "plugins/pvio/pvio_npipe.c",
        "plugins/pvio/pvio_shmem.c",
        "plugins/pvio/pvio_socket.c",
    ],
    hdrs = glob([
        "plugins/pvio/**/*.h",
    ]),
    visibility = ["//visibility:private"],
    deps = [":mariadb-hdrs"],
)

cc_library(
    name = "mariadb-plugin-connection",
    srcs = [
        "plugins/connection/aurora.c",
        "plugins/connection/replication.c",
    ],
    hdrs = glob([
        "plugins/pvio/**/*.h",
    ]),
    visibility = ["//visibility:private"],
    deps = [":mariadb-hdrs"],
)

cc_library(
    name = "mariadb",
    srcs = [
        "libmariadb/ma_alloc.c",
        "libmariadb/ma_array.c",
        "libmariadb/ma_charset.c",
        "libmariadb/ma_compress.c",
        "libmariadb/ma_context.c",
        "libmariadb/ma_default.c",
        "libmariadb/ma_dtoa.c",
        "libmariadb/ma_errmsg.c",
        "libmariadb/ma_hash.c",
        "libmariadb/ma_init.c",
        "libmariadb/ma_io.c",
        "libmariadb/ma_list.c",
        "libmariadb/ma_ll2str.c",
        "libmariadb/ma_loaddata.c",
        "libmariadb/ma_net.c",
        "libmariadb/ma_password.c",
        "libmariadb/ma_pvio.c",
        "libmariadb/ma_sha1.c",
        "libmariadb/ma_stmt_codec.c",
        "libmariadb/ma_string.c",
        "libmariadb/ma_time.c",
        "libmariadb/ma_tls.c",
        "libmariadb/mariadb_async.c",
        "libmariadb/mariadb_charset.c",
        "libmariadb/mariadb_lib.c",
        "libmariadb/mariadb_rpl.c",
        "libmariadb/mariadb_stmt.c",
    ] + ["@//sources:ma_client_plugin_c"],
    copts = [
        "-DHAVE_COMPRESS",
        "-DLIBMARIADB",
        "-DTHREAD",
    ],
    visibility = ["//visibility:public"],
    deps = [
        ":mariadb-hdrs",
        ":mariadb-plugin-auth",
        ":mariadb-plugin-connection",
        ":mariadb-plugin-pvio",
        ":zlib",
    ],
)
