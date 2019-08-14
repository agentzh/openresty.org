<!---
    @title         Components
    @creator       Yichun Zhang
    @created       2011-06-21 04:24 GMT
--->

Below lists all the components bundled in [OpenResty](openresty.html). All of
the components can be enabled or disabled as needed.

Most of the components are enabled by default, but some are not.

[DrizzleNginxModule](drizzle-nginx-module.html),
[PostgresNginxModule](postgres-nginx-module.html), and
[IconvNginxModule](iconv-nginx-module.html) are not enabled by default. You
need to specify the `--with-http_drizzle_module`,
`--with-http_postgres_module`, and `--with-http_iconv_module` options,
respectively, to enable them while [building OpenResty](installation.html).

Before the 1.5.8.1 release, the standard Lua 5.1 interpreter is enabled by
default while [LuaJIT](luajit.html) 2.x is not. So for earlier releases, you
need to explicitly specify the `--with-luajit` option (which is the default for
1.5.8.1+) to use [LuaJIT](luajit.html) 2.x.

Since the 1.15.8.1 release, the standard Lua 5.1 interpreter is not supported
anymore. It is vividly recommended to use [OpenResty's branch of
LuaJIT](https://github.com/openresty/luajit2) (already bundled and enabled by
default in [OpenResty](openresty.html) releases since 1.5.8.1). This fork is
regularly synchronized with the upstream LuaJIT repository, receives timely
fixes, and implements additional features proper to
[OpenResty](openresty.html).

* [LuaJIT](luajit.html)
* [ArrayVarNginxModule](array-var-nginx-module.html)
* [AuthRequestNginxModule](auth-request-nginx-module.html)
* [CoolkitNginxModule](coolkit-nginx-module.html)
* [DrizzleNginxModule](drizzle-nginx-module.html)
* [EchoNginxModule](echo-nginx-module.html)
* [EncryptedSessionNginxModule](encrypted-session-nginx-module.html)
* [FormInputNginxModule](form-input-nginx-module.html)
* [HeadersMoreNginxModule](headers-more-nginx-module.html)
* [IconvNginxModule](iconv-nginx-module.html)
* [StandardLuaInterpreter](standard-lua-interpreter.html)
* [MemcNginxModule](memc-nginx-module.html)
* [Nginx](nginx.html)
* [NginxDevelKit](nginx-devel-kit.html)
* [LuaCjsonLibrary](lua-cjson-library.html)
* [LuaNginxModule](lua-nginx-module.html)
* [LuaRdsParserLibrary](lua-rds-parser-library.html)
* [LuaRedisParserLibrary](lua-redis-parser-library.html)
* [LuaRestyCoreLibrary](lua-resty-core-library.html)
* [LuaRestyDNSLibrary](lua-resty-dns-library.html)
* [LuaRestyLockLibrary](lua-resty-lock-library.html)
* [LuaRestyLrucacheLibrary](lua-resty-lrucache-library.html)
* [LuaRestyMemcachedLibrary](lua-resty-memcached-library.html)
* [LuaRestyMySQLLibrary](lua-resty-mysql-library.html)
* [LuaRestyRedisLibrary](lua-resty-redis-library.html)
* [LuaRestyStringLibrary](lua-resty-string-library.html)
* [LuaRestyUploadLibrary](lua-resty-upload-library.html)
* [LuaRestyUpstreamHealthcheckLibrary](lua-resty-upstream-healthcheck-library.html)
* [LuaRestyWebSocketLibrary](lua-resty-web-socket-library.html)
* [LuaRestyLimitTrafficLibrary](https://github.com/openresty/lua-resty-limit-traffic)
* [LuaRestyShellLibrary](https://github.com/openresty/lua-resty-shell)
* [LuaRestySignalLibrary](https://github.com/openresty/lua-resty-signal)
* [LuaTablePoolLibrary](https://github.com/openresty/lua-tablepool)
* [LuaUpstreamNginxModule](lua-upstream-nginx-module.html)
* [OPM](https://github.com/openresty/opm#readme)
* [PostgresNginxModule](postgres-nginx-module.html)
* [RdsCsvNginxModule](rds-csv-nginx-module.html)
* [RdsJsonNginxModule](rds-json-nginx-module.html)
* [RedisNginxModule](redis-nginx-module.html)
* [Redis2NginxModule](redis-2-nginx-module.html)
* [RestyCLI](resty-cli.html)
* [SetMiscNginxModule](set-misc-nginx-module.html)
* [SrcacheNginxModule](srcache-nginx-module.html)
* [StreamLuaNginxModule](https://github.com/openresty/stream-lua-nginx-module#readme)
* [XssNginxModule](xss-nginx-module.html)

3rd-party OpenResty modules contributed by the community can be found on the [opm.openresty.org](https://opm.openresty.org)
package server. And they can also be installed and uninstalled easily with the [opm](https://github.com/openresty/opm#readme)
command-line utility.
