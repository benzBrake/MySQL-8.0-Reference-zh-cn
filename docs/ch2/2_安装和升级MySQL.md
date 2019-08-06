# 第2章 安装和升级MySQL
本章节介绍如何获取和安装MySQL。以下是程序的摘要，后面的部分提供了详细信息。 如果您计划将现有版本的MySQL升级到较新版本而不是首次安装MySQL，请参阅第2.11节“升级MySQL”，了解有关升级过程以及升级前应考虑的问题的信息。

如果你想迁移其他数据库到MySQL，请参阅第八章 “MySQL 8.0 FAQ: 迁移”，该章节包括迁移相关问题的解答。

## MySQL的安装通常需要遵循以下步骤

### 确定MySQL是否可以在您的平台上运行并受支持。

请注意，并非所有平台都可以运行MySQL，而且并非所有运行MySQL的平台都由Oracle Corporation正式支持。 有关官方支持的平台的信息，请参阅MySQL网站：https://www.mysql.com/support/supportedplatforms/database.html。

### 选择安装的版本

多个版本的MySQL可用，多数都有几种分发格式。 您可以从包含二进制（预编译）发行版或源代码的预打包发行版中进行选择。不知如何选择？请使用二进制发行版。 Oracle还为那些想要查看最新开发和测试新代码的人提供了MySQL源代码包。 要确定应使用的版本和分发类型，请参阅第2.1.1节“要安装的MySQL版本和分发版本”。

### 下载需要安装的发行版

请参阅第2.1.2节“如何获取MySQL”。 要验证分发的完整性，请使用第2.1.3节“使用MD5校验和或GnuPG验证程序包完整性”中的说明。

### 安装MySQL

如果想安装二进制发行版MySQL，请参阅第2.2节，“在Unix/Linux上安装二进制发行版MySQL”.

要从源代码分发版或当前开发源代码安装MySQL，请使用第2.9节“从源代码安装MySQL”中的说明。

### 执行任何必要的安装后设置

安装MySQL后，请参阅第2.10节“安装后设置和测试”以获取有关确保MySQL服务器正常工作的信息。 另请参阅第2.10.4节“保护初始MySQL帐户”中提供的信息。 本节介绍如何保护初始MySQL root用户帐户，该帐户在分配密码之前没有密码。 无论您是使用二进制文件还是源代码分发安装MySQL，本节均适用。

如果要运行MySQL benchmark脚本，必须提供对MySQL的Perl支持。 请参阅第2.13节“Perl安装说明”。

### 在不同平台和环境中安装MySQL

* UNIX，LINUX，FreeBSD

使用通用二进制文件（例如：`.tar.gz`压缩包）在大多数Linux和Unix平台上安装MySQL，请参见第2.2节“使用通用二进制文件在Unix / Linux上安装MySQL”。

有关从源代码发行版或源代码库完全构建MySQL的信息，请参见第2.9节“从源代码安装MySQL”

有关从源代码安装，配置和构建的特定平台版本，请参阅相应的平台部分：

* Linux，包括有关分发特定方法的说明，请参见第2.5节“在Linux上安装MySQL”。

* IBM AIX，请参见第2.7节“在Solaris上安装MySQL”。

* FreeBSD，参见第2.8节“在FreeBSD中安装MySQL”。

* Microsoft Windows

有关在Microsoft Windows上安装MySQL的说明，请使用MySQL 安装包或zip压缩二进制文件，请参见第2.3节“在Microsoft Windows上安装MySQL”。

有关管理MySQL实例的信息，请参阅MySQL Notifier Overview。

有关使用Microsoft Visual Studio从源代码构建MySQL的详细信息和说明，请参见第2.9节“从源代码安装MySQL”。

* OS X

要在OS X上安装，包括使用二进制包和PKG安装包，请参见第2.4节“在macOS上安装MySQL”。

有关使用OS X Launch Daemon自动启动和停止MySQL的信息，请参见第2.4.3节“安装和使用MySQL启动守护程序”。

有关MySQL 首选项面板的信息，请参见第2.4.4节“安装和使用MySQL 首选项面板”。