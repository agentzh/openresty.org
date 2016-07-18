<!---
    @title         RPM Packages
--->

OpenResty 官方 Yum 资源库提供下面的 PRM 包。

# openresty

这是用于核心 OpenResty 服务的生产版本。

这个包注册在 `/usr/bin/openresty`, 它是 OpenResty 的 `nginx` 可执行文件 `/usr/local/openresty/nginx/sbin/nginx` 的符号链接。 默认的，你应该能在你的 `PATH` 环境变量中看到 `openresty` 命令。当你想调用这个包提供的 nginx 可执行文件时，记得总是用 `openresty` 而不是 `nginx`。 `nginx` 默认并不在你的 `PATH` 环境变量中，这是为了避免和同一个系统中其他 NGINX 包发生冲突。

你可以使用这个命令来启动默认的 OpenResty 服务

```
sudo /sbin/service openresty start
```

 `stop`, `restart`, 和 `reload` 这些指令也是支持的。

默认的服务前缀是 `/usr/local/openresty/`。对于你自己的 OpenResty 应用，强烈推荐指定你自己的前缀，并指向你自己应用的目录，像这样：

```
sudo openresty -p /opt/my-fancy-app/
```

Then you have sub-directories like `conf/`, `html/` and `logs/` under the `/opt/my-fancy-app/` directory.
This way, we can avoid polluting the OpenResty installation trees under `/usr/local/openresty/` and allow
multiple different OpenResty applications sharing the same OpenResty server installation. You will need
to draft up a init script for each of your OpenResty application yourself, however. You can use the default
`/etc/init.d/openresty` init script as a template.

This package enables the dtrace static probes in the NGINX core and some NGINX C modules (like `ngx_http_lua_module`),
which can be consumed by dynamic tracing tools like SystemTap.

We use our own builds of OpenSSL (through the `openresty-openssl` package), PCRE, zlib, and LuaJIT to ensure these
critical components are up to date and well formed.

# openresty-resty

This package contains the `resty` command-line utility, which is visible to your `PATH` environment (as
`/usr/bin/resty`. To try it out, just type

```console
$ resty -e 'ngx.say("hello")'
hello
```

This package depends on the standard `perl` package and our `openresty` package to work properly.

See the [resty-cli](https://github.com/openresty/resty-cli) project for more details.

# openresty-doc

This package contains the OpenResty documentation tool chain and documentation data. The most useful tool
is the `restydoc` command-line utility, which should be visible to your `PATH` environment by default (as
`/usr/bin/restydoc`.

To try it out:

```bash
restydoc ngx_lua

restydoc -s content_by_lua

restydoc -s proxy_pass
```

See the output of the `restydoc -h` command for more details on its usage.

For the best result, please ensure your terminal is using the UTF-8 character encoding and both of your `perl`
and `groff` installations are modern enough. Otherwise those non-ASCII characters may not be displayed
correctly.

# openresty-debug

This is the normal debug build of OpenResty. As compared to the `openresty` package, it has the following
differences:

* It disables C compiler optimizations in the build.
* It enables the NGINX debugging log capability.
* It uses the `openresty-openssl-debug` package instead of `openresty-openssl` for the OpenSSL library.
* It enables API checks and assertions in the LuaJIT build.
* It enables the assertions in the `ngx_http_lua` module.
* It makes the `ngx_http_lua` module abort the current nginx worker process immediately upon LuaJIT allocation
failures in its GC-managed memory (the default behavior is logging an error message and gracefully quit
the current worker process).
* The default server prefix of its NGINX is `/usr/local/openresty-debug/`.
* The entry point visible to your `PATH` environment is `openresty-debug` instead of `openresty`.
* It does not come with a init script.

You should never use this package in production. This package is for development only.

# openresty-valgrind

This is a special debug version of OpenResty targeting the Valgrind tool chain. Valgrind is a powerful tool
to check various kinds of memory issues, like memory leaks and memory invalid accesses. To maximize the
possibilities of catching memory bugs via Valgrind, this build does the following in addition to those
done in the `openresty-debug` package:

* It disables the memory pools used in the NGINX by applying the "[no-pool](https://github.com/openresty/no-pool-nginx)" patch.
* It enforces LuaJIT to use the system allocator instead of its own.
* It enables the internal Valgrind co-operations in the LuaJIT build.
* The default server prefix of its NGINX is `/usr/local/openresty-valgrind/`.
* The entry point visible to your `PATH` environment is `openresty-valgrind` instead of `openresty-debug`.

See the following tutorials on more details on Valgrind-based testing in the context of OpenResty:

https://openresty.gitbooks.io/programming-openresty/content/testing/test-modes.html#_valgrind_mode

# openresty-openssl

This is our own build of the OpenSSL library. In particular, we have disabled the threads support in the build
to save some overhead.

# openresty-openssl-debug

This is the debug build of OpenSSL library. As compared to `openresty-openssl`, it has the following changes:

* It disables any C compiler optimizations.
* It relies on the libefence library of the standard `ElectricFence` package to do extra checks.
* It is Valgrind clean and free of any Valgrind false positives.
* Assembly code is disabled so we always have perfect C-land backtraces and etc.

# perl-Test-Nginx

This is our [Test::Nginx](https://github.com/openresty/test-nginx) test framework. Read the following book chapter on a complete
introduction to this test scaffold:

https://openresty.gitbooks.io/programming-openresty/content/testing/

# Debuginfo Packages

We provide debuginfo packages for those containing binary components like the `openresty` and `openresty-openssl` packages. Their
debuginfo packages just have the `-debuginfo` suffix in their package names, just like other standard RPM packages.

# Source

The source files used to build these packages can be found in the `openresty-packaging` GitHub repository:

https://github.com/openresty/openresty-packaging/tree/master/rpm/

# See Also

See the [Linux Packages](linux-packages.html) page for more details on our official OpenResty package repositories.
