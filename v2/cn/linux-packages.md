<!---
    @title         OpenResty® Linux 包
--->

对于下列 Linux 发行版的种类和版本号，OpenResty<sup>&reg;</sup> 提供官方的预编译包。

* Ubuntu

```
    版本            版本名         支持的体系结构
    14.04           Trusty          amd64, i386
    16.04           Xenial          amd64, i386
    16.10           Yakkety         amd64, i386
    17.04           Zesty           amd64, i386
    17.10           Artful          amd64, i386
```

* CentOS

```
    版本号         支持的体系结构
    6.x             x86_64
    7.x             x86_64
```

* Red Hat 企业版本 Linux (RHEL)

```
    版本号          支持的体系结构
    6.x             x86_64
    7.x             x86_64
```

* Fedora

```
    版本号          支持的体系结构
    24              x86_64
    25              x86_64
    26              x86_64
```

* 亚马逊 Linux

```
    版本号         支持的体系结构
    2017.03         x86_64
```

我们仓库的所有元数据和二进制包都是用下面的 GPG 密钥， `0xD5EDEB74` 签名的：
https://openresty.org/package/pubkey.gpg

唯一的区别是 Ubuntu 的 PPA 仓库。他们用的 GPG key 是 `2E61F1063ED1B4FD`。

# Ubuntu

你可以在你的 Ubuntu 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum update` 命令）。
运行下面的命令就可以添加我们的仓库：+You can add the `openresty` repository to your Ubuntu system so as to easily install

```bash
sudo apt-get -y install software-properties-common
sudo add-apt-repository -y ppa:openresty/ppa
```

然后就可以像下面这样安装包了，比如装 `openresty`：

```bash
    sudo apt-get install openresty
```

这个包同时也推荐安装 `openresty-opm` 和 `openresty-restydoc` 包，所以后面两个包会缺省安装上。
如果你不想自动关联安装，可以用下面方法关闭自动关联安装：

```bash
    sudo apt-get install --no-install-recommends openresty
```

参阅 [OpenResty Deb 包](deb-packages.html) 页面获取这个仓库里头更多可用包的信息。

# CentOS

你可以在你的 CentOS 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum update` 命令）。运行下面的命令就可以添加我们的仓库：

```bash
    sudo yum install yum-utils
    sudo yum-config-manager --add-repo https://openresty.org/package/centos/openresty.repo
```

然后就可以像下面这样安装软件包，比如 `openresty`：

```bash
    sudo yum install openresty
```

如果你想安装命令行工具 `resty`，那么可以像下面这样安装 `openresty-resty` 包：

```bash
    sudo yum install openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出所有 `openresty` 仓库里头的软件包：

```bash
    sudo yum --disablerepo="*" --enablerepo="openresty" list available
```

参考 [OpenResty RPM 包](rpm-packages.html)页面获取这些包更多的细节。

# RHEL

你可以在你的 RHEL 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum update` 命令）。添加仓库，运行下面的命令：

```bash
    sudo yum install yum-utils
    sudo yum-config-manager --add-repo https://openresty.org/package/rhel/openresty.repo
```

在想 RHEL 6.x 这样的老系统上，最后那条命令可能因为 `yum-config-manager` 命令的内部问题，生成下面的错误：

```
    [Errno 14] Peer cert cannot be verified or peer cert invalid
```

如果出现上述问题，你可以用下面的命令添加仓库：


```bash
    sudo yum-config-manager --add-repo http://openresty.org/package/rhel/openresty.repo
```

添加了包仓库之后就可以像下面这样安装软件包，比如 `openresty`：

```bash
    sudo yum install openresty
```

如果你想安装命令行工具 `resty`，那么可以像下面这样安装 `openresty-resty` 包：

```bash
    sudo yum install openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出所有 `openresty` 仓库里头的软件包：

```bash
    sudo yum --disablerepo="*" --enablerepo="openresty" list available
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

# Fedora

在 Fedora 系统中你可以这样来启用 `openresty` 仓库:

```bash
    sudo dnf install dnf-plugins-core
    sudo dnf config-manager --add-repo https://openresty.org/package/fedora/openresty.repo
```

然后你就可以方便的从 `openresty-openresty` 仓库中安装和更新包(通过 `dnf update` 命令)。 比如我们可以运行下面的命令来安装 `openresty`:

```bash
sudo dnf install openresty
```

如果想安装 `resty` 命令行工具，则像下面这样安装 `openresty-resty` 软件包：

```bash
    sudo dnf install openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出在 `openresty-openresty` 仓库中所有可用的包, 可以这样

```bash
sudo dnf repo-pkgs openresty-openresty list available
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

# 亚马逊 Linux

你可以在你的 亚马逊 Linux 系统里头用下面命令添加 `openresty` 仓库：

```bash
    sudo yum install yum-utils
    sudo yum-config-manager --add-repo https://openresty.org/package/amazon/openresty.repo
```

然后你就可以像下面这样安装包了，比如说安装 `openresty`：

```bash
    sudo yum install openresty
```

如果想安装 `resty` 命令行工具，则像下面这样安装 `openresty-resty` 软件包：

```bash
    sudo dnf install openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出在 `openresty-openresty` 仓库中所有可用的包, 可以这样

```bash
sudo dnf repo-pkgs openresty-openresty list available
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

# 更多 Linux 发行版的支持

我们欢迎社区贡献更多的 Linux 发行版，比如 OpenSuse 和 Debian 的打包源。请确保新的安装包尽可能地接近我们现有的 [RPM 安装包](rpm-packages.html)。非常感谢！

# 非 Linux 系统的安装包

目前 OpenResty 也提供针对 Windows 系统的二进制安装包，可以从[下载页面](download.html)获取。
