# 第一章 总体信息

MySQL™软件提供了非常快速，多线程，多用户且健壮的SQL（结构化查询语言）数据库服务器。 MySQL Server 适用于关键任务，高负荷的生产系统以及嵌入到大规模部署的软件中。 Oracle 是 Oracle Corporation 或其分支机构的注册商标。 MySQL 是Oracle Corporation 或其分支机构的商标，未经 Oracle 明确的书面授权，客户不得使用MySQL。 其他名称可能是其各自所有者的商标。

MySQL软件是双重许可的。 用户可以选择根据GNU通用公共许可证（[http://www.fsf.org/licenses/](http://www.fsf.org/licenses/)）的条款将MySQL软件用作开放源代码产品，也可以从 Oracle 购买标准的商业许可证。 有关我们的许可政策的更多信息，详见 [http://www.mysql.com/company/legal/licensing/](http://www.mysql.com/company/legal/licensing/) 。

以下列表描述了本手册中特别有趣的章节：
- 有关 MySQL 数据库服务器功能的讨论, 详见 [节 1.3.2, “The Main Features of MySQL”](#features). 
- 有关 MySQL 新功能的概述, 详见 [节 1.4, “What Is New in MySQL 8.0”](#mysql-nutshell). 
- For information about the changes in each version, see the [Release Notes](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/). 
- ​For installation instructions, see [Chapter 2, *Installing and Upgrading MySQL*](installing). For information about upgrading MySQL, see [Section 2.11, “Upgrading MySQL”](installing#upgrading) 
- ​For a tutorial introduction to the MySQL Database Server, see [Chapter 3, *Tutorial*](tutorial). 
- For information about configuring and administering MySQL Server, see [Chapter 5, *MySQL Server Administration*](server-administration). 
- For information about security in MySQL, see [Chapter 6, *Security*](security). 
- For information about setting up replication servers, see [Chapter 17, *Replication*](replication). 
- For information about MySQL Enterprise, the commercial MySQL release with advanced features and management tools, see [Chapter 30, *MySQL Enterprise Edition*](mysql-enterprise). 
- For answers to a number of questions that are often asked concerning the MySQL Database Server and its capabilities, see [Appendix A, *MySQL 8.0 Frequently Asked Questions*](faqs). 
- For a history of new features and bug fixes, see the [Release Notes](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/).


 > **重要说明**
 > 
 > 要报告问题或错误，请使用[第1.7节“如何报告错误或问题”](＃bug-reports)中的说明。 如果您发现 MySQL Server 中的安全错误，请通过将电子邮件发送到<secalert_us@oracle.com>来立即通知我们。 例外：支持客户应向 Oracle 支持部门报告所有问题，包括安全错误。

## 1.1 关于手册

这是8.0.23版之前的MySQL数据库系统8.0版的参考手册。 本文中以发行版本号（8.0.*`x` *）指出了MySQL 8.0的次要版本之间的差异。有关许可证的信息，请参见[法律声明](preface.md#法律声明)。

​ This manual is not intended for use with older versions of the MySQL software due to the many functional and other differences between MySQL 8.0 and previous versions. If you are using an earlier release of the MySQL software, please refer to the appropriate manual. For example, [*MySQL 5.7 Reference Manual*](https://dev.mysql.com/doc/refman/5.7/en/) covers the 5.7 series of MySQL software releases. 

​ Because this manual serves as a reference, it does not provide general instruction on SQL or relational database concepts. It also does not teach you how to use your operating system or command-line interpreter. 

​ The MySQL Database Software is under constant development, and the Reference Manual is updated frequently as well. The most recent version of the manual is available online in searchable form at https://dev.mysql.com/doc/. Other formats also are available there, including HTML, PDF, and EPUB versions. 



​ The Reference Manual source files are written in DocBook XML format. The HTML version and other formats are produced automatically, primarily using the DocBook XSL stylesheets. For information about DocBook, see http://docbook.org/ 

​ The source code for MySQL itself contains internal documentation written using Doxygen. The generated Doxygen content is available https://dev.mysql.com/doc/index-other.html. It is also possible to generate this content locally from a MySQL source distribution using the instructions at [Section 2.9.10, “Generating MySQL Doxygen Documentation Content”](installing#source-installation-doxygen). 

​ If you have questions about using MySQL, join the [MySQL Community Slack](https://mysqlcommunity.slack.com/), or ask in our forums; see [Section 1.6.2, “MySQL Community Support at the MySQL Forums”](#forums). If you have suggestions concerning additions or corrections to the manual itself, please send them to the http://www.mysql.com/company/contact/. 

​ This manual was originally written by David Axmark and Michael “Monty” Widenius. It is maintained by the MySQL Documentation Team, consisting of Chris Cole, Paul DuBois, Margaret Fisher, Edward Gilmore, Stefan Hinz, David Moss, Philip Olson, Daniel Price, Daniel So, and Jon Stephens.

## 1.2 格式和语法说明

本手册编写采用以下约定

- `普通代码` 用于SQL语句、数据库名称、表明、列名、程序清单、源代码和环境变量；比如: 使用 [`FLUSH PRIVILEGES`](sql-statements.md#flush-privileges) 指令来刷新 grant 赋权结果。
- **`加粗代码`** 指示您在示例中输入的内容。
- **加粗文本** indicates the names of executable programs and scripts, examples being [**mysql**](programs#mysql) (the MySQL command-line client program) and [**mysqld**](programs#mysqld) (the MySQL server executable). 
- *`斜体代码`* is used for variable input for which you should substitute a value of your own choosing. 
- *斜体文本* is used for emphasis. 
- **加粗文本** is used in table headings and to convey especially strong emphasis. 
- `Text in this style` is used to indicate a program option that affects how the program is executed, or that supplies information that is needed for the program to function in a certain way. *Example*: “The `--host` option (short form `-h`) tells the [**mysql**](programs#mysql) client program the hostname or IP address of the MySQL server that it should connect to”. 
- File names and directory names are written like this: “The global `my.cnf` file is located in the `/etc` directory.” 
- Character sequences are written like this: “To specify a wildcard, use the ‘`%`’ character.”

命令前边如果存在提示符则说明命令需要在指定执行环境中运行。 例如， `shell>` 说明您命令需要从登录 shell 执行，root-shell>`说明命令需要以 root 用户执行，而`mysql>`说明命令需要在 MySQL 终端中执行：

```
shell> shell 语句
root-shell> 以 root 用户执行 shell 语句
mysql> SQL 语句
```

在某些章节，可能会将不同的系统区分开来，以表明命令应在两个不同的环境中执行。 例如，在进行复制时，命令可能以`master`和`slave`为前缀：

```
master> 需要在主节点执行的命令
slave> 需要在从节点执行的命令
```

`shell` 是你的命令解释器。在 Unix 中，通常是**sh**, **csh** 或 **bash**。在 Windows 中, 类似的程序有 **command.com** 或者 **cmd.exe**, 通常在终端窗口中运行。

​ When you enter a command or statement shown in an example, do not type the prompt shown in the example. 

​ Database, table, and column names must often be substituted into statements. To indicate that such substitution is necessary, this manual uses *`db_name`*, *`tbl_name`*, and *`col_name`*. For example, you might see a statement like this: 

```
mysql> SELECT col_name FROM db_name.tbl_name;
```

​ This means that if you were to enter a similar statement, you would supply your own database, table, and column names, perhaps like this: 

```
mysql> SELECT author_name FROM biblio_db.author_list;
```

​ SQL keywords are not case-sensitive and may be written in any lettercase. This manual uses uppercase. 

​ In syntax descriptions, square brackets (“`[`” and “`]`”) indicate optional words or clauses. For example, in the following statement, `IF EXISTS` is optional: 

```
DROP TABLE [IF EXISTS] tbl_name
```

​ When a syntax element consists of a number of alternatives, the alternatives are separated by vertical bars (“`|`”). When one member from a set of choices *may* be chosen, the alternatives are listed within square brackets (“`[`” and “`]`”): 

```
TRIM([[BOTH | LEADING | TRAILING] [remstr] FROM] str)
```

​ When one member from a set of choices *must* be chosen, the alternatives are listed within braces (“`{`” and “`}`”): 

```
{DESCRIBE | DESC} tbl_name [col_name | wild]
```

​ An ellipsis (`...`) indicates the omission of a section of a statement, typically to provide a shorter version of more complex syntax. For example, [`SELECT ... INTO  OUTFILE`](sql-statements.html#select) is shorthand for the form of [`SELECT`](sql-statements.html#select) statement that has an `INTO OUTFILE` clause following other parts of the statement. 

​ An ellipsis can also indicate that the preceding syntax element of a statement may be repeated. In the following example, multiple *`reset_option`* values may be given, with each of those after the first preceded by commas: 

```
RESET reset_option [,reset_option] ...
```

​ Commands for setting shell variables are shown using Bourne shell syntax. For example, the sequence to set the `CC` environment variable and run the **configure** command looks like this in Bourne shell syntax: 

```
shell> CC=gcc ./configure
```



如果你使用的是 **csh** 或者 **tcsh**，you must issue commands somewhat differently: 

```
shell> setenv CC gcc
shell> ./configure
```

## 1.3 MySQL 数据库管理系统概述

- [1.3.1 MySQL 是啥?](#_131-mysql-是啥)
- [1.3.2 MySQL 的主要特性](#features)
- [1.3.3 History of MySQL](#history)

### 1.3.1 MySQL 是啥?

MySQL是最流行的开源SQL数据库管理系统，由 Oracle Corporation 开发，分发和支持。

MySQL网站[http://www.mysql.com/]http://www.mysql.com/)提供有关MySQL软件的最新信息。

- ** MySQL是一个数据库管理系统。**

数据库是结构化的数据集合。 从简单的购物清单到图片库，或者企业网络中的大量信息，它都可以是任何东西。 要添加，访问和处理存储在计算机数据库中的数据，您需要一个数据库管理系统，例如MySQL Server。 由于计算机非常擅长处理大量数据，因此数据库管理系统作为独立实用程序或其他应用程序的一部分，在计算中起着核心作用。

- ** MySQL数据库是关系数据库。**

关系数据库将数据存储在单独的表中，而不是将所有数据放在一个库中。数据库结构被组织成针对速度进行了优化的物理文件。具有对象（例如数据库，表，视图，行和列）的逻辑模型提供了灵活的编程环境。您可以设置规则来管理不同数据字段之间的关系，例如一对一，一对多，唯一，必需或可选以及不同表之间的“指针”。数据库强制执行这些规则，因此，使用设计良好的数据库，您的应用程序将永远不会看到不一致，重复，孤立，孤立，过时或丢失的数据。

 ​ The SQL part of “MySQL” stands for “Structured Query Language”. SQL is the most common standardized language used to access databases. Depending on your programming environment, you might enter SQL directly (for example, to generate reports), embed SQL statements into code written in another language, or use a language-specific API that hides the SQL syntax. 

 ​ SQL is defined by the ANSI/ISO SQL Standard. The SQL standard has been evolving since 1986 and several versions exist. In this manual, “SQL-92” refers to the standard released in 1992, “SQL:1999” refers to the standard released in 1999, and “SQL:2003” refers to the current version of the standard. We use the phrase “the SQL standard” to mean the current version of the SQL Standard at any time. 

- **MySQL software is Open Source.** 

 ​ Open Source means that it is possible for anyone to use and modify the software. Anybody can download the MySQL software from the Internet and use it without paying anything. If you wish, you may study the source code and change it to suit your needs. The MySQL software uses the GPL (GNU General Public License), http://www.fsf.org/licenses/, to define what you may and may not do with the software in different situations. If you feel uncomfortable with the GPL or need to embed MySQL code into a commercial application, you can buy a commercially licensed version from us. See the MySQL Licensing Overview for more information (http://www.mysql.com/company/legal/licensing/). 

- **The MySQL Database Server is very fast, reliable, scalable, and easy to use.** 

 ​ If that is what you are looking for, you should give it a try. MySQL Server can run comfortably on a desktop or laptop, alongside your other applications, web servers, and so on, requiring little or no attention. If you dedicate an entire machine to MySQL, you can adjust the settings to take advantage of all the memory, CPU power, and I/O capacity available. MySQL can also scale up to clusters of machines, networked together. 

 ​ MySQL Server was originally developed to handle large databases much faster than existing solutions and has been successfully used in highly demanding production environments for several years. Although under constant development, MySQL Server today offers a rich and useful set of functions. Its connectivity, speed, and security make MySQL Server highly suited for accessing databases on the Internet. 

- **MySQL Server works in client/server or embedded systems.** 

 ​ The MySQL Database Software is a client/server system that consists of a multithreaded SQL server that supports different back ends, several different client programs and libraries, administrative tools, and a wide range of application programming interfaces (APIs). 

 ​ We also provide MySQL Server as an embedded multithreaded library that you can link into your application to get a smaller, faster, easier-to-manage standalone product. 

- **A large amount of contributed MySQL software is available.** 

 ​ MySQL Server has a practical set of features developed in close cooperation with our users. It is very likely that your favorite application or language supports the MySQL Database Server.


​ The official way to pronounce “MySQL” is “My Ess Que Ell” (not “my sequel”), but we do not mind if you pronounce it as “my sequel” or in some other localized way.

### 1.3.2 MySQL 的主要特性

本节描述了MySQL数据库软件的一些重要特征。 在大多数方面，该路线图适用于所有版本的MySQL。 有关按系列特定功能引入MySQL的功能的信息，请参见相应手册的“特性”部分：

- MySQL 8.0: [节 1.4, “MySQL 8.0 有什么新特性”](#_14-MySQL-80-有什么新特性) 
- MySQL 5.7: [MySQL 5.7 有什么新特性](https://dev.mysql.com/doc/refman/5.7/en/mysql-nutshell.html) 
- MySQL 5.6: [MySQL 5.6 有什么新特性](https://dev.mysql.com/doc/refman/5.6/en/mysql-nutshell.html)

#### 内部说明和便携性

- 使用 C 和 C++ 编写. 
- 广泛的经过不同编译器测试。
- 在不同平台上都能运行详见 [https://www.mysql.com/support/supportedplatforms/database.html]()。 
- For portability, configured using **CMake**. 
- Tested with Purify (a commercial memory leakage detector) as well as with Valgrind, a GPL tool (http://developer.kde.org/~sewardj/). 
- Uses multi-layered server design with independent modules. 
- Designed to be fully multithreaded using kernel threads, to easily use multiple CPUs if they are available. 
- Provides transactional and nontransactional storage engines. 
- Uses very fast B-tree disk tables (`MyISAM`) with index compression. 
- Designed to make it relatively easy to add other storage engines. This is useful if you want to provide an SQL interface for an in-house database. 
- Uses a very fast thread-based memory allocation system. 
- Executes very fast joins using an optimized nested-loop join. 
- Implements in-memory hash tables, which are used as temporary tables. 
- Implements SQL functions using a highly optimized class library that should be as fast as possible. Usually there is no memory allocation at all after query initialization. 
- Provides the server as a separate program for use in a client/server networked environment, and as a library that can be embedded (linked) into standalone applications. Such applications can be used in isolation or in environments where no network is available.

#### Data Types

- Many data types: signed/unsigned integers 1, 2, 3, 4, and 8 bytes long, [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types), [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types), [`CHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char), [`VARCHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char), [`BINARY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#binary-varbinary), [`VARBINARY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#binary-varbinary), [`TEXT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob), [`BLOB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob), [`DATE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime), [`TIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#time), [`DATETIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime), [`TIMESTAMP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime), [`YEAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#year), [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set), [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum), and OpenGIS spatial types. See [Chapter 11, *Data Types*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html). 
- Fixed-length and variable-length string types.

#### Statements and Functions

- Full operator and function support in the [`SELECT`](sql-statements.html#select) list and `WHERE` clause of queries. For example: 

 ```
 mysql> SELECT CONCAT(first_name, ' ', last_name)
 -> FROM citizen
 -> WHERE income/dependents > 10000 AND age > 30;
 ```

- Full support for SQL `GROUP BY` and `ORDER BY` clauses. Support for group functions ([`COUNT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_count), [`AVG()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_avg), [`STD()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_std), [`SUM()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_sum), [`MAX()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_max), [`MIN()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_min), and [`GROUP_CONCAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_group-concat)). 

- Support for `LEFT OUTER JOIN` and `RIGHT OUTER JOIN` with both standard SQL and ODBC syntax. 

- Support for aliases on tables and columns as required by standard SQL. 

- Support for [`DELETE`](sql-statements.html#delete), [`INSERT`](sql-statements.html#insert), [`REPLACE`](sql-statements.html#replace), and [`UPDATE`](sql-statements.html#update) to return the number of rows that were changed (affected), or to return the number of rows matched instead by setting a flag when connecting to the server. 

- Support for MySQL-specific [`SHOW`](sql-statements.html#show) statements that retrieve information about databases, storage engines, tables, and indexes. Support for the `INFORMATION_SCHEMA` database, implemented according to standard SQL. 

- An [`EXPLAIN`](sql-statements.html#explain) statement to show how the optimizer resolves a query. 

- Independence of function names from table or column names. For example, `ABS` is a valid column name. The only restriction is that for a function call, no spaces are permitted between the function name and the “`(`” that follows it. See [Section 9.3, “Keywords and Reserved Words”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/language-structure.html#keywords). 

- You can refer to tables from different databases in the same statement.

#### 安全

- A privilege and password system that is very flexible and secure, and that enables host-based verification. 
- Password security by encryption of all password traffic when you connect to a server.

#### Scalability and Limits

- Support for large databases. We use MySQL Server with databases that contain 50 million records. We also know of users who use MySQL Server with 200,000 tables and about 5,000,000,000 rows. 
- Support for up to 64 indexes per table. Each index may consist of 1 to 16 columns or parts of columns. The maximum index width for [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) tables is either 767 bytes or 3072 bytes. See [Section 15.22, “InnoDB Limits”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-limits). The maximum index width for [`MyISAM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/storage-engines.html#myisam-storage-engine) tables is 1000 bytes. See [Section 16.2, “The MyISAM Storage Engine”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/storage-engines.html#myisam-storage-engine). An index may use a prefix of a column for [`CHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char), [`VARCHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char), [`BLOB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob), or [`TEXT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob) column types.

#### Connectivity

- Clients can connect to MySQL Server using several protocols:
 - Clients can connect using TCP/IP sockets on any platform.  
 - On Windows systems, clients can connect using named pipes if the server is started with the [`named_pipe`](server-administration#sysvar_named_pipe) system variable enabled. Windows servers also support shared-memory connections if started with the [`shared_memory`](server-administration#sysvar_shared_memory) system variable enabled. Clients can connect through shared memory by using the [`--protocol=memory`](programs#option_general_protocol) option.  
 - On Unix systems, clients can connect using Unix domain socket files.
- MySQL client programs can be written in many languages. A client library written in C is available for clients written in C or C++, or for any language that provides C bindings. 
- APIs for C, C++, Eiffel, Java, Perl, PHP, Python, Ruby, and Tcl are available, enabling MySQL clients to be written in many languages. See [Chapter 28, *Connectors and APIs*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/connectors-apis.html). 
- The Connector/ODBC (MyODBC) interface provides MySQL support for client programs that use ODBC (Open Database Connectivity) connections. For example, you can use MS Access to connect to your MySQL server. Clients can be run on Windows or Unix. Connector/ODBC source is available. All ODBC 2.5 functions are supported, as are many others. See [MySQL Connector/ODBC Developer Guide](https://dev.mysql.com/doc/connector-odbc/en/). 
- The Connector/J interface provides MySQL support for Java client programs that use JDBC connections. Clients can be run on Windows or Unix. Connector/J source is available. See [MySQL Connector/J 5.1 Developer Guide](https://dev.mysql.com/doc/connector-j/5.1/en/). 
- MySQL Connector/NET enables developers to easily create .NET applications that require secure, high-performance data connectivity with MySQL. It implements the required ADO.NET interfaces and integrates into ADO.NET aware tools. Developers can build applications using their choice of .NET languages. MySQL Connector/NET is a fully managed ADO.NET driver written in 100% pure C#. See [MySQL Connector/NET Developer Guide](https://dev.mysql.com/doc/connector-net/en/).

#### 本地化

- The server can provide error messages to clients in many languages. See [Section 10.12, “Setting the Error Message Language”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/charset.html#error-message-language). 
- Full support for several different character sets, including `latin1` (cp1252), `german`, `big5`, `ujis`, several Unicode character sets, and more. For example, the Scandinavian characters “`å`”, “`ä`” and “`ö`” are permitted in table and column names. 
- All data is saved in the chosen character set. 
- Sorting and comparisons are done according to the default character set and collation. is possible to change this when the MySQL server is started (see [Section 10.3.2, “Server Character Set and Collation”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/charset.html#charset-server)). To see an example of very advanced sorting, look at the Czech sorting code. MySQL Server supports many different character sets that can be specified at compile time and runtime. 
- The server time zone can be changed dynamically, and individual clients can specify their own time zone. See [Section 5.1.14, “MySQL Server Time Zone Support”](server-administration#time-zone-support).

#### 客户端和工具

- MySQL includes several client and utility programs. These include both command-line programs such as [**mysqldump**](programs#mysqldump) and [**mysqladmin**](programs#mysqladmin), and graphical programs such as [MySQL Workbench](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/workbench.html). 
- MySQL Server has built-in support for SQL statements to check, optimize, and repair tables. These statements are available from the command line through the [**mysqlcheck**](programs#mysqlcheck) client. MySQL also includes [**myisamchk**](programs#myisamchk), a very fast command-line utility for performing these operations on `MyISAM` tables. See [Chapter 4, *MySQL Programs*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/programs.html). 
- MySQL programs can be invoked with the `--help` or `-?` option to obtain online assistance.

### 1.3.3 MySQL 的历史



​ We started out with the intention of using the `mSQL` database system to connect to our tables using our own fast low-level (ISAM) routines. However, after some testing, we came to the conclusion that `mSQL` was not fast enough or flexible enough for our needs. This resulted in a new SQL interface to our database but with almost the same API interface as `mSQL`. This API was designed to enable third-party code that was written for use with `mSQL` to be ported easily for use with MySQL. 

​ MySQL is named after co-founder Monty Widenius's daughter, My. 

​ The name of the MySQL Dolphin (our logo) is “Sakila,” which was chosen from a huge list of names suggested by users in our “Name the Dolphin” contest. The winning name was submitted by Ambrose Twebaze, an Open Source software developer from Eswatini (formerly Swaziland), Africa. According to Ambrose, the feminine name Sakila has its roots in SiSwati, the local language of Eswatini. Sakila is also the name of a town in Arusha, Tanzania, near Ambrose's country of origin, Uganda.

## 1.4 MySQL 8.0 有什么新特性

​ This section summarizes what has been added to, deprecated in, and removed from MySQL 8.0. A companion section lists MySQL server options and variables that have been added, deprecated, or removed in MySQL 8.0. See [Section 1.5, “Server and Status Variables and Options Added, Deprecated, or Removed in  MySQL 8.0”](#added-deprecated-removed).

- [Features Added in MySQL 8.0](#mysql-nutshell-additions) 
- [Features Deprecated in MySQL 8.0](#mysql-nutshell-deprecations) 
- [Features Removed in MySQL 8.0](#mysql-nutshell-removals)

### Features Added in MySQL 8.0



​ The following features have been added to MySQL 8.0:

- **Data dictionary.** MySQL now incorporates a transactional data dictionary that stores information about database objects. In previous MySQL releases, dictionary data was stored in metadata files and nontransactional tables. For more information, see [Chapter 14, *MySQL Data Dictionary*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-dictionary.html).  

 

 

- **Atomic data definition statements (Atomic DDL).** An atomic DDL statement combines the data dictionary updates, storage engine operations, and binary log writes associated with a DDL operation into a single, atomic transaction. For more information, see [Section 13.1.1, “Atomic Data Definition Statement Support”](sql-statements.html#atomic-ddl).  

 

 

- **Upgrade procedure.** Previously, after installation of a new version of MySQL, the MySQL server automatically upgrades the data dictionary tables at the next startup, after which the DBA is expected to invoke [**mysql_upgrade**](programs#mysql-upgrade) manually to upgrade the system tables in the `mysql` schema, as well as objects in other schemas such as the `sys` schema and user schemas.  

 

 

 ​  As of MySQL 8.0.16, the server performs the tasks previously  handled by [**mysql_upgrade**](programs#mysql-upgrade). After  installation of a new MySQL version, the server now  automatically performs all necessary upgrade tasks at the  next startup and is not dependent on the DBA invoking  [**mysql_upgrade**](programs#mysql-upgrade). In addition, the server  updates the contents of the help tables (something  [**mysql_upgrade**](programs#mysql-upgrade) did not do). A new  [`--upgrade`](server-administration#option_mysqld_upgrade) server option  provides control over how the server performs automatic data  dictionary and server upgrade operations. For more  information, see  [Section 2.11.3, “What the MySQL Upgrade Process Upgrades”](installing#upgrading-what-is-upgraded). 

- **Security and account management.** These enhancements were added to improve security and enable greater DBA flexibility in account management:

 

 

 - The grant tables in the `mysql` system database are now `InnoDB` (transactional) tables. Previously, these were `MyISAM` (nontransactional) tables. The change of grant table storage engine underlies an accompanying change to the behavior of account-management statements. Previously, an account-management statement (such as [`CREATE USER`](sql-statements.html#create-user) or [`DROP USER`](sql-statements.html#drop-user)) that named multiple users could succeed for some users and fail for others. Now, each statement is transactional and either succeeds for all named users or rolls back and has no effect if any error occurs. The statement is written to the binary log if it succeeds, but not if it fails; in that case, rollback occurs and no changes are made. For more information, see [Section 13.1.1, “Atomic Data Definition Statement Support”](sql-statements.html#atomic-ddl). 

 - A new `caching_sha2_password` authentication plugin is available. Like the `sha256_password` plugin, `caching_sha2_password` implements SHA-256 password hashing, but uses caching to address latency issues at connect time. It also supports more transport protocols and does not require linking against OpenSSL for RSA key pair-based password-exchange capabilities. See [Section 6.4.1.2, “Caching SHA-2 Pluggable Authentication”](security#caching-sha2-pluggable-authentication). 

 ​ The `caching_sha2_password` and `sha256_password` authentication plugins provide more secure password encryption than the `mysql_native_password` plugin, and `caching_sha2_password` provides better performance than `sha256_password`. Due to these superior security and performance characteristics of `caching_sha2_password`, it is now the preferred authentication plugin, and is also the default authentication plugin rather than `mysql_native_password`. For information about the implications of this change of default plugin for server operation and compatibility of the server with clients and connectors, see [caching_sha2_password as the Preferred Authentication Plugin](installing#upgrade-caching-sha2-password). 

 - MySQL now supports roles, which are named collections of privileges. Roles can be created and dropped. Roles can have privileges granted to and revoked from them. Roles can be granted to and revoked from user accounts. The active applicable roles for an account can be selected from among those granted to the account, and can be changed during sessions for that account. For more information, see [Section 6.2.10, “Using Roles”](security#roles). 

 - MySQL now incorporates the concept of user account categories, with system and regular users distinguished according to whether they have the [`SYSTEM_USER`](security#priv_system-user) privilege. See [Section 6.2.11, “Account Categories”](security#account-categories). 

 - Previously, it was not possible to grant privileges that apply globally except for certain schemas. This is now possible if the [`partial_revokes`](server-administration#sysvar_partial_revokes) system variable is enabled. See [Section 6.2.12, “Privilege Restriction Using Partial Revokes”](security#partial-revokes). 

 - The [`GRANT`](sql-statements.html#grant) statement has an `AS *`user`* [WITH ROLE]` clause that specifies additional information about the privilege context to use for statement execution. This syntax is visible at the SQL level, although its primary purpose is to enable uniform replication across all nodes of grantor privilege restrictions imposed by partial revokes, by causing those restrictions to appear in the binary log. See [Section 13.7.1.6, “GRANT Statement”](sql-statements.html#grant). 

 - MySQL now maintains information about password history, enabling restrictions on reuse of previous passwords. DBAs can require that new passwords not be selected from previous passwords for some number of password changes or period of time. It is possible to establish password-reuse policy globally as well as on a per-account basis. 

 ​ It is now possible to require that attempts to change account passwords be verified by specifying the current password to be replaced. This enables DBAs to prevent users from changing password without proving that they know the current password. It is possible to establish password-verification policy globally as well as on a per-account basis. 

 ​ Accounts are now permitted to have dual passwords, which enables phased password changes to be performed seamlessly in complex multiple-server systems, without downtime. 

 ​ MySQL now enables administrators to configure user accounts such that too many consecutive login failures due to incorrect passwords cause temporary account locking. The required number of failures and the lock time are configurable per account. 

 ​ These new capabilities provide DBAs more complete control over password management. For more information, see [Section 6.2.15, “Password Management”](security#password-management). 

 - MySQL now supports FIPS mode, if compiled using OpenSSL, and an OpenSSL library and FIPS Object Module are available at runtime. FIPS mode imposes conditions on cryptographic operations such as restrictions on acceptable encryption algorithms or requirements for longer key lengths. See [Section 6.6, “FIPS Support”](security#fips-mode). 

 - The TLS context the server uses for new connections now is reconfigurable at runtime. This capability may be useful, for example, to avoid restarting a MySQL server that has been running so long that its SSL certificate has expired. See [Server-Side Runtime Configuration and Monitoring for Encrypted Connections](security#using-encrypted-connections-server-side-runtime-configuration). 

 - OpenSSL 1.1.1 supports the TLS v1.3 protocol for encrypted connections, and MySQL 8.0.16 and higher supports TLS v1.3 as well, if both the server and client are compiled using OpenSSL 1.1.1 or higher. See [Section 6.3.2, “Encrypted Connection TLS Protocols and Ciphers”](security#encrypted-connection-protocols-ciphers). 

 - MySQL now sets the access control granted to clients on the named pipe to the minimum necessary for successful communication on Windows. Newer MySQL client software can open named pipe connections without any additional configuration. If older client software cannot be upgraded immediately, the new [`named_pipe_full_access_group`](server-administration#sysvar_named_pipe_full_access_group) system variable can be used to give a Windows group the necessary permissions to open a named pipe connection. Membership in the full-access group should be restricted and temporary.

- **Resource management.** MySQL now supports creation and management of resource groups, and permits assigning threads running within the server to particular groups so that threads execute according to the resources available to the group. Group attributes enable control over its resources, to enable or restrict resource consumption by threads in the group. DBAs can modify these attributes as appropriate for different workloads. Currently, CPU time is a manageable resource, represented by the concept of “virtual CPU” as a term that includes CPU cores, hyperthreads, hardware threads, and so forth. The server determines at startup how many virtual CPUs are available, and database administrators with appropriate privileges can associate these CPUs with resource groups and assign threads to groups. For more information, see [Section 5.1.15, “Resource Groups”](server-administration#resource-groups).  

 

 

- **Table encryption management.** Table encryption can now be managed globally by defining and enforcing encryption defaults. The [`default_table_encryption`](server-administration#sysvar_default_table_encryption) variable defines an encryption default for newly created schemas and general tablespace. The encryption default for a schema can also be defined using the `DEFAULT ENCRYPTION` clause when creating a schema. By default, a table inherits the encryption of the schema or general tablespace it is created in. Encryption defaults are enforced by enabling the [`table_encryption_privilege_check`](server-administration#sysvar_table_encryption_privilege_check) variable. The privilege check occurs when creating or altering a schema or general tablespace with an encryption setting that differs from the [`default_table_encryption`](server-administration#sysvar_default_table_encryption) setting, or when creating or altering a table with an encryption setting that differs from the default schema encryption. The [`TABLE_ENCRYPTION_ADMIN`](security#priv_table-encryption-admin) privilege permits overriding default encryption settings when [`table_encryption_privilege_check`](server-administration#sysvar_table_encryption_privilege_check) is enabled. For more information, see [Defining an Encryption Default for Schemas and General Tablespaces](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-schema-tablespace-encryption-default).  

 

 

- **InnoDB enhancements.** These `InnoDB` enhancements were added:

 

 

 - The current maximum auto-increment counter value is written to the redo log each time the value changes, and saved to an engine-private system table on each checkpoint. These changes make the current maximum auto-increment counter value persistent across server restarts. Additionally:

 - A server restart no longer cancels the effect of the `AUTO_INCREMENT = N` table option. If you initialize the auto-increment counter to a specific value, or if you alter the auto-increment counter value to a larger value, the new value is persisted across server restarts. 
 - A server restart immediately following a [`ROLLBACK`](sql-statements.html#commit) operation no longer results in the reuse of auto-increment values that were allocated to the rolled-back transaction. 
 - If you modify an `AUTO_INCREMENT` column value to a value larger than the current maximum auto-increment value (in an [`UPDATE`](sql-statements.html#update) operation, for example), the new value is persisted, and subsequent [`INSERT`](sql-statements.html#insert) operations allocate auto-increment values starting from the new, larger value.

 ​ For more information, see [Section 15.6.1.6, “AUTO_INCREMENT Handling in InnoDB”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-auto-increment-handling), and [InnoDB AUTO_INCREMENT Counter Initialization](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-auto-increment-initialization). 

 - When encountering index tree corruption, `InnoDB` writes a corruption flag to the redo log, which makes the corruption flag crash safe. `InnoDB` also writes in-memory corruption flag data to an engine-private system table on each checkpoint. During recovery, `InnoDB` reads corruption flags from both locations and merges results before marking in-memory table and index objects as corrupt. 

 - The `InnoDB` **memcached** plugin supports multiple `get` operations (fetching multiple key-value pairs in a single **memcached** query) and range queries. See [Section 15.20.4, “InnoDB memcached Multiple get and Range Query Support”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-memcached-multiple-get-range-query). 

 - A new dynamic variable, [`innodb_deadlock_detect`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_deadlock_detect), may be used to disable deadlock detection. On high concurrency systems, deadlock detection can cause a slowdown when numerous threads wait for the same lock. At times, it may be more efficient to disable deadlock detection and rely on the [`innodb_lock_wait_timeout`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_lock_wait_timeout) setting for transaction rollback when a deadlock occurs. 

 

 

 - The new [`INFORMATION_SCHEMA.INNODB_CACHED_INDEXES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-cached-indexes-table) table reports the number of index pages cached in the `InnoDB` buffer pool for each index. 

 - `InnoDB` temporary tables are now created in the shared temporary tablespace, `ibtmp1`. 

 - The `InnoDB` [tablespace encryption feature](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-data-encryption) supports encryption of redo log and undo log data. See [Redo Log Encryption](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-data-encryption-redo-log), and [Undo Log Encryption](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-data-encryption-undo-log). 

 - `InnoDB` supports `NOWAIT` and `SKIP LOCKED` options with `SELECT ... FOR SHARE` and `SELECT ... FOR UPDATE` locking read statements. `NOWAIT` causes the statement to return immediately if a requested row is locked by another transaction. `SKIP LOCKED` removes locked rows from the result set. See [Locking Read Concurrency with NOWAIT and SKIP LOCKED](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-locking-reads-nowait-skip-locked). 

 ​ `SELECT ... FOR SHARE` replaces `SELECT ... LOCK IN SHARE MODE`, but `LOCK IN SHARE MODE` remains available for backward compatibility. The statements are equivalent. However, `FOR UPDATE` and `FOR SHARE` support `NOWAIT`, `SKIP LOCKED`, and `OF *`tbl_name`*` options. See [Section 13.2.10, “SELECT Statement”](sql-statements.html#select). 

 ​ `OF *`tbl_name`*` applies locking queries to named tables. 

 - `ADD PARTITION`, `DROP PARTITION`, `COALESCE PARTITION`, `REORGANIZE PARTITION`, and `REBUILD PARTITION` [`ALTER TABLE`](sql-statements.html#alter-table) options are supported by native partitioning in-place APIs and may be used with `ALGORITHM={COPY|INPLACE}` and `LOCK` clauses. 

 ​ `DROP PARTITION` with `ALGORITHM=INPLACE` deletes data stored in the partition and drops the partition. However, `DROP PARTITION` with `ALGORITHM=COPY` or [`old_alter_table=ON`](server-administration#sysvar_old_alter_table) rebuilds the partitioned table and attempts to move data from the dropped partition to another partition with a compatible `PARTITION ... VALUES` definition. Data that cannot be moved to another partition is deleted. 

 - The `InnoDB` storage engine now uses the MySQL data dictionary rather than its own storage engine-specific data dictionary. For information about the data dictionary, see [Chapter 14, *MySQL Data Dictionary*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-dictionary.html). 

 - `mysql` system tables and data dictionary tables are now created in a single `InnoDB` tablespace file named `mysql.ibd` in the MySQL data directory. Previously, these tables were created in individual `InnoDB` tablespace files in the `mysql` database directory. 

 - The following undo tablespace changes are introduced in MySQL 8.0:

 - By default, undo logs now reside in two undo tablespaces that are created when the MySQL instance is initialized. Undo logs are no longer created in the system tablespace. 

 - As of MySQL 8.0.14, additional undo tablespaces can be created in a chosen location at runtime using [`CREATE UNDO TABLESPACE`](sql-statements.html#create-tablespace) syntax. 

 ```
 CREATE UNDO TABLESPACE tablespace_name ADD DATAFILE 'file_name.ibu';
 ```

 ​ Undo tablespaces created using [`CREATE UNDO TABLESPACE`](sql-statements.html#create-tablespace) syntax can be dropped at runtime using [`DROP UNDO TABLESPACE`](sql-statements.html#drop-tablespace) syntax. 

 ```
 DROP UNDO TABLESPACE tablespace_name;
 ```

 ​ [`ALTER UNDO TABLESPACE`](sql-statements.html#alter-tablespace) syntax can be used to mark an undo tablespace as active or inactive. 

 ```
 ALTER UNDO TABLESPACE tablespace_name SET {ACTIVE|INACTIVE};
 ```

 ​ A `STATE` column that shows the state of a tablespace was added to the [`INFORMATION_SCHEMA.INNODB_TABLESPACES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-tablespaces-table) table. An undo tablespace must be in an `empty` state before it can be dropped. 

 - The [`innodb_undo_log_truncate`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_undo_log_truncate) variable is enabled by default. 

 - The [`innodb_rollback_segments`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_rollback_segments) variable defines the number of rollback segments per undo tablespace. Previously, [`innodb_rollback_segments`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_rollback_segments) specified the total number of rollback segments for the MySQL instance. This change increases the number of rollback segments available for concurrent transactions. More rollback segments increases the likelihood that concurrent transactions use separate rollback segments for undo logs, resulting in less resource contention.

 - Default values for variables that affect buffer pool preflushing and flushing behavior were modified:

 - The [`innodb_max_dirty_pages_pct_lwm`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_max_dirty_pages_pct_lwm) default value is now 10. The previous default value of 0 disables buffer pool preflushing. A value of 10 enables preflushing when the percentage of dirty pages in the buffer pool exceeds 10%. Enabling preflushing improves performance consistency. 
 - The [`innodb_max_dirty_pages_pct`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_max_dirty_pages_pct) default value was increased from 75 to 90. `InnoDB` attempts to flush data from the buffer pool so that the percentage of dirty pages does not exceed this value. The increased default value permits a greater percentage of dirty pages in the buffer pool.

 - The default [`innodb_autoinc_lock_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_autoinc_lock_mode) setting is now 2 (interleaved). Interleaved lock mode permits the execution of multi-row inserts in parallel, which improves concurrency and scalability. The new [`innodb_autoinc_lock_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_autoinc_lock_mode) default setting reflects the change from statement-based replication to row based replication as the default replication type in MySQL 5.7. Statement-based replication requires the consecutive auto-increment lock mode (the previous default) to ensure that auto-increment values are assigned in a predictable and repeatable order for a given sequence of SQL statements, whereas row-based replication is not sensitive to the execution order of SQL statements. For more information, see [InnoDB AUTO_INCREMENT Lock Modes](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-auto-increment-lock-modes). 

 ​ For systems that use statement-based replication, the new [`innodb_autoinc_lock_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_autoinc_lock_mode) default setting may break applications that depend on sequential auto-increment values. To restore the previous default, set [`innodb_autoinc_lock_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_autoinc_lock_mode) to 1. 

 - Renaming a general tablespace is supported by [`ALTER TABLESPACE ... RENAME TO`](sql-statements.html#alter-tablespace) syntax. 

 - The new [`innodb_dedicated_server`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_dedicated_server) variable, which is disabled by default, can be used to have `InnoDB` automatically configure the following options according to the amount of memory detected on the server:

 - [`innodb_buffer_pool_size`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_buffer_pool_size) 
 - [`innodb_log_file_size`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_log_file_size) 
 - [`innodb_flush_method`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_flush_method)

 ​ This option is intended for MySQL server instances that run on a dedicated server. For more information, see [Section 15.8.12, “Enabling Automatic Configuration for a Dedicated MySQL Server”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-dedicated-server). 

 - The new [`INFORMATION_SCHEMA.INNODB_TABLESPACES_BRIEF`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-tablespaces-brief-table) view provides space, name, path, flag, and space type data for `InnoDB` tablespaces. 

 - The [zlib library](http://www.zlib.net/) version bundled with MySQL was raised from version 1.2.3 to version 1.2.11. MySQL implements compression with the help of the zlib library. 

 ​ If you use `InnoDB` compressed tables, see [Section 2.11.4, “Changes in MySQL 8.0”](installing#upgrading-from-previous-series) for related upgrade implications. 

 - Serialized dictionary information (SDI) is present in all `InnoDB` tablespace files except for global temporary tablespace and undo tablespace files. SDI is serialized metadata for table and tablespace objects. The presence of SDI data provides metadata redundancy. For example, dictionary object metadata may be extracted from tablespace files if the data dictionary becomes unavailable. SDI extraction is performed using the [**ibd2sdi**](programs#ibd2sdi) tool. SDI data is stored in `JSON` format. 

 ​ The inclusion of SDI data in tablespace files increases tablespace file size. An SDI record requires a single index page, which is 16KB in size by default. However, SDI data is compressed when it is stored to reduce the storage footprint. 

 - The `InnoDB` storage engine now supports atomic DDL, which ensures that DDL operations are either fully committed or rolled back, even if the server halts during the operation. For more information, see [Section 13.1.1, “Atomic Data Definition Statement Support”](sql-statements.html#atomic-ddl). 

 - Tablespace files can be moved or restored to a new location while the server is offline using the [`innodb_directories`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_directories) option. For more information, see [Section 15.6.3.6, “Moving Tablespace Files While the Server is Offline”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-moving-data-files-offline). 

 - The following redo logging optimizations were implemented:

 - User threads can now write concurrently to the log buffer without synchronizing writes. 
 - User threads can now add dirty pages to the flush list in a relaxed order. 
 - A dedicated log thread is now responsible for writing the log buffer to the system buffers, flushing system buffers to disk, notifying user threads about written and flushed redo, maintaining the lag required for the relaxed flush list order, and write checkpoints. 
 - System variables were added for configuring the use of spin delay by user threads waiting for flushed redo:
 - [`innodb_log_wait_for_flush_spin_hwm`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_log_wait_for_flush_spin_hwm): Defines the maximum average log flush time beyond which user threads no longer spin while waiting for flushed redo. 
 - [`innodb_log_spin_cpu_abs_lwm`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_log_spin_cpu_abs_lwm): Defines the minimum amount of CPU usage below which user threads no longer spin while waiting for flushed redo. 
 - [`innodb_log_spin_cpu_pct_hwm`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_log_spin_cpu_pct_hwm): Defines the maximum amount of CPU usage above which user threads no longer spin while waiting for flushed redo.
 - The [`innodb_log_buffer_size`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_log_buffer_size) variable is now dynamic, which permits resizing of the log buffer while the server is running.

 ​ For more information, see [Section 8.5.4, “Optimizing InnoDB Redo Logging”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizing-innodb-logging). 

 - As of MySQL 8.0.12, undo logging is supported for small updates to large object (LOB) data, which improves performance of LOB updates that are 100 bytes in size or less. Previously, LOB updates were a minimum of one LOB page in size, which is less than optimal for updates that might only modify a few bytes. This enhancement builds upon support added in MySQL 8.0.4 for partial update of LOB data. 

 - As of MySQL 8.0.12, `ALGORITHM=INSTANT` is supported for the following [`ALTER TABLE`](sql-statements.html#alter-table) operations:

 - Adding a column. This feature is also referred to as “Instant `ADD COLUMN`”. Limitations apply. See [Section 15.12.1, “Online DDL Operations”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-online-ddl-operations). 
 - Adding or dropping a virtual column. 
 - Adding or dropping a column default value. 
 - Modifying the definition of an [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum) or [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set) column. 
 - Changing the index type. 
 - Renaming a table.

 ​ Operations that support `ALGORITHM=INSTANT` only modify metadata in the data dictionary. No metadata locks are taken on the table, and table data is unaffected, making the operations instantaneous. If not specified explicitly, `ALGORITHM=INSTANT` is used by default by operations that support it. If `ALGORITHM=INSTANT` is specified but not supported, the operation fails immediately with an error. 

 ​ For more information about operations that support `ALGORITHM=INSTANT`, see [Section 15.12.1, “Online DDL Operations”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-online-ddl-operations). 

 - As of MySQL 8.0.13, the `TempTable` storage engine supports storage of binary large object (BLOB) type columns. This enhancement improves performance for queries that use temporary tables containing BLOB data. Previously, temporary tables that contained BLOB data were stored in the on-disk storage engine defined by [`internal_tmp_disk_storage_engine`](server-administration#sysvar_internal_tmp_disk_storage_engine). For more information, see [Section 8.4.4, “Internal Temporary Table Use in MySQL”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#internal-temporary-tables). 

 - As of MySQL 8.0.13, the `InnoDB` data-at-rest encryption feature supports general tablespaces. Previously, only file-per-table tablespaces could be encrypted. To support encryption of general tablespaces, [`CREATE TABLESPACE`](sql-statements.html#create-tablespace) and [`ALTER TABLESPACE`](sql-statements.html#alter-tablespace) syntax was extended to include an `ENCRYPTION` clause. 

 ​ The [`INFORMATION_SCHEMA.INNODB_TABLESPACES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-tablespaces-table) table now includes an `ENCRYPTION` column that indicates whether or not a tablespace is encrypted. 

 ​ The `stage/innodb/alter tablespace (encryption)` Performance Schema stage instrument was added to permit monitoring of general tablespace encryption operations. 

 - Disabling the `innodb_buffer_pool_in_core_file` variable reduces the size of core files by excluding `InnoDB` buffer pool pages. To use this variable, the [`core_file`](server-administration#sysvar_core_file) variable must be enabled and the operating system must support the `MADV_DONTDUMP` non-POSIX extension to `madvise()`, which is supported in Linux 3.4 and later. For more information, see [Section 15.8.3.7, “Excluding Buffer Pool Pages from Core Files”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-buffer-pool-in-core-file). 

 - As of MySQL 8.0.13, user-created temporary tables and internal temporary tables created by the optimizer are stored in session temporary tablespaces that are allocated to a session from a pool of temporary tablespaces. When a session disconnects, its temporary tablespaces are truncated and released back to the pool. In previous releases, temporary tables were created in the global temporary tablespace (`ibtmp1`), which did not return disk space to the operating system after temporary tables were dropped. 

 ​ The [`innodb_temp_tablespaces_dir`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_temp_tablespaces_dir) variable defines the location where session temporary tablespaces are created. The default location is the `#innodb_temp` directory in the data directory. 

 ​ The [`INNODB_SESSION_TEMP_TABLESPACES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-session-temp-tablespaces-table) table provides metadata about session temporary tablespaces. 

 ​ The global temporary tablespace (`ibtmp1`) now stores rollback segments for changes made to user-created temporary tables. 

 - As of MySQL 8.0.14, `InnoDB` supports parallel clustered index reads, which can improve [`CHECK TABLE`](sql-statements.html#check-table) performance. This feature does not apply to secondary index scans. The [`innodb_parallel_read_threads`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_parallel_read_threads) session variable must be set to a value greater than 1 for parallel clustered index reads to occur. The default value is 4. The actual number of threads used to perform a parallel clustered index read is determined by the [`innodb_parallel_read_threads`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_parallel_read_threads) setting or the number of index subtrees to scan, whichever is smaller. 

 - As of 8.0.14, when the [`innodb_dedicated_server`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_dedicated_server) variable is enabled, the size and number of log files are configured according to the automatically configured buffer pool size. Previously, log file size was configured according to the amount of memory detected on the server, and the number of log files was not configured automatically. 

 - As of 8.0.14, the `ADD DATAFILE` clause of the [`CREATE TABLESPACE`](sql-statements.html#create-tablespace) statement is optional, which permits users without the [`FILE`](security#priv_file) privilege to create tablespaces. A [`CREATE TABLESPACE`](sql-statements.html#create-tablespace) statement executed without an `ADD DATAFILE` clause implicitly creates a tablespace data file with a unique file name. 

 - By default, when the amount of memory occupied by the TempTable storage engine exceeds the memory limit defined by the [`temptable_max_ram`](server-administration#sysvar_temptable_max_ram) variable, the TempTable storage engine begins allocating memory-mapped temporary files from disk. As of MySQL 8.0.16, this behavior is controlled by the [`temptable_use_mmap`](server-administration#sysvar_temptable_use_mmap) variable. Disabling [`temptable_use_mmap`](server-administration#sysvar_temptable_use_mmap) causes the TempTable storage engine to use `InnoDB` on-disk internal temporary tables instead of memory-mapped files as its overflow mechanism. For more information, see [Internal Temporary Table Storage Engine](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#internal-temporary-tables-engines). 

 - As of MySQL 8.0.16, the `InnoDB` data-at-rest encryption feature supports encryption of the `mysql` system tablespace. The `mysql` system tablespace contains the `mysql` system database and the MySQL data dictionary tables. For more information, see [Section 15.13, “InnoDB Data-at-Rest Encryption”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-data-encryption). 

 - The [`innodb_spin_wait_pause_multiplier`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_spin_wait_pause_multiplier) variable, introduced in MySQL 8.0.16, provides greater control over the duration of spin-lock polling delays that occur when a thread waits to acquire a mutex or rw-lock. Delays can be tuned more finely to account for differences in PAUSE instruction duration on different processor architectures. For more information, see [Section 15.8.8, “Configuring Spin Lock Polling”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-performance-spin_lock_polling). 

 - `InnoDB` parallel read thread performance for large data sets was improved in MySQL 8.0.17 through better utilization of read threads, through a reduction in read thread I/O for prefetch activity that occurs during parallel scans, and through support for parallel scanning of partitions. 

 ​ The parallel read thread feature is controlled by the [`innodb_parallel_read_threads`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_parallel_read_threads) variable. The maximum setting is now 256, which is the total number of threads for all client connections. If the thread limit is reached, connections fall back to using a single thread. 

 - The [`innodb_idle_flush_pct`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_idle_flush_pct) variable, introduced in MySQL 8.0.18, permits placing a limit on page flushing during idle periods, which can help extend the life of solid state storage devices. See [Limiting Buffer Flushing During Idle Periods](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-limit-flushing-rate). 

 - Efficient sampling of `InnoDB` data for the purpose of generating histogram statistics is supported as of MySQL 8.0.19. See [Histogram Statistics Analysis](sql-statements.html#analyze-table-histogram-statistics-analysis). 

 - As of MySQL 8.0.20, the doublewrite buffer storage area resides in doublewrite files. In previous releases, the storage area resided in the system tablespace. Moving the storage area out of the system tablespace reduces write latency, increases throughput, and provides flexibility with respect to placement of doublewrite buffer pages. The following system variables were introduced for advanced doublewrite buffer configuration:

 - [`innodb_doublewrite_dir`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_doublewrite_dir) 

 ​ Defines the doublewrite buffer file directory. 

 - [`innodb_doublewrite_files`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_doublewrite_files) 

 ​ Defines the number of doublewrite files. 

 - [`innodb_doublewrite_pages`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_doublewrite_pages) 

 ​ Defines the maximum number of doublewrite pages per thread for a batch write. 

 - [`innodb_doublewrite_batch_size`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_doublewrite_batch_size) 

 ​ Defines the number of doublewrite pages to write in a batch.

 ​ For more information, see [Section 15.6.4, “Doublewrite Buffer”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-doublewrite-buffer). 

 - The Contention-Aware Transaction Scheduling (CATS) algorithm, which prioritizes transactions that are waiting for locks, was improved in MySQL 8.0.20. Transaction scheduling weight computation is now performed a separate thread entirely, which improves computation performance and accuracy. 

 ​ The First In First Out (FIFO) algorithm, which had also been used for transaction scheduling, was removed. The FIFO algorithm was rendered redundant by CATS algorithm enhancements. Transaction scheduling previously performed by the FIFO algorithm is now performed by the CATS algorithm. 

 ​ A `TRX_SCHEDULE_WEIGHT` column was added to the `INFORMATION_SCHEMA.INNODB_TRX` table, which permits querying transaction scheduling weights assigned by the CATS algorithm. 

 ​ The following `INNODB_METRICS` counters were added for monitoring code-level transaction scheduling events:

 - `lock_rec_release_attempts` 

 ​ The number of attempts to release record locks. 

 - `lock_rec_grant_attempts` 

 ​ The number of attempts to grant record locks. 

 - `lock_schedule_refreshes` 

 ​ The number of times the wait-for graph was analyzed to update transaction schedule weights.

 ​ For more information, see [Section 15.7.6, “Transaction Scheduling”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-transaction-scheduling). 

 - As of MySQL 8.0.21, to improve concurrency for operations that require access to lock queues for table and row resources, the lock system mutex (`lock_sys->mutex`) was replaced in by sharded latches, and lock queues were grouped into table and page *lock queue shards*, with each shard protected by a dedicated mutex. Previously, the single lock system mutex protected all lock queues, which was a point of contention on high-concurrency systems. The new sharded implementation permits more granular access to lock queues. 

 ​ The lock system mutex (`lock_sys->mutex`) was replaced by the following sharded latches:

 - A global latch (`lock_sys->latches.global_latch`) consisting of 64 read-write lock objects (`rw_lock_t`). Access to an individual lock queue requires a shared global latch and a latch on the lock queue shard. Operations that require access to all lock queues take an exclusive global latch, which latches all table and page lock queue shards. 
 - Table shard latches (`lock_sys->latches.table_shards.mutexes`), implemented as an array of 512 mutexes, with each mutex dedicated to one of 512 table lock queue shards. 
 - Page shard latches (`lock_sys->latches.page_shards.mutexes`), implemented as an array of 512 mutexes, with each mutex dedicated to one of 512 page lock queue shards.

 ​ The Performance Schema `wait/synch/mutex/innodb/lock_mutex` instrument for monitoring the single lock system mutex was replaced by instruments for monitoring the new global, table shard, and page shard latches:

 - `wait/synch/sxlock/innodb/lock_sys_global_rw_lock` 
 - `wait/synch/mutex/innodb/lock_sys_table_mutex` 
 - `wait/synch/mutex/innodb/lock_sys_page_mutex`

-  As of MySQL 8.0.21, table and table partition data files  created outside of the data directory using the  `DATA DIRECTORY` clause are restricted to  directories known to `InnoDB`. This change  permits database administrators to control where tablespace  data files are created and ensures that the data files can  be found during recovery. 

 ​  General and file-per-table tablespaces data files  (`.ibd` files) can no longer be created  in the undo tablespace directory  ([`innodb_undo_directory`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_undo_directory))  unless that directly is known to `InnoDB`. 

 ​  Known directories are those defined by the  [`datadir`](server-administration#sysvar_datadir),  [`innodb_data_home_dir`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_data_home_dir), and  [`innodb_directories`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_directories)  variables. 

 ​  Truncating an `InnoDB` table that resides  in a file-per-table tablespace drops the existing tablespace  and creates a new one. As of MySQL 8.0.21,  `InnoDB` creates the new tablespace in the  default location and writes a warning to the error log if  the current tablespace directory is unknown. To have  [`TRUNCATE TABLE`](sql-statements.html#truncate-table) create the  tablespace in its current location, add the directory to the  [`innodb_directories`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_directories) setting  before running [`TRUNCATE TABLE`](sql-statements.html#truncate-table). 

-  As of MySQL 8.0.21, redo logging can be enabled and disabled  using [`ALTER INSTANCE {ENABLE|DISABLE} INNODB REDO_LOG`](sql-statements.html#alter-instance) syntax.  This functionality is intended for loading data into a new  MySQL instance. Disabling redo logging helps speed up data  loading by avoiding redo log writes. 

 ​  The new  [`INNODB_REDO_LOG_ENABLE`](security#priv_innodb-redo-log-enable)  privilege permits enabling and disabling redo logging. 

 ​  The new  [`Innodb_redo_log_enabled`](server-administration#statvar_Innodb_redo_log_enabled)  status variable permits monitoring redo logging status. 

 ​  See [Disabling Redo Logging](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-disable-redo-logging). 

-  At startup, `InnoDB` validates the paths of  known tablespace files against tablespace file paths stored  in the data dictionary in case tablespace files have been  moved to a different location. The new  [`innodb_validate_tablespace_paths`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_validate_tablespace_paths)  variable, introduced in MySQL 8.0.21, permits disabling  tablespace path validation. This feature is intended for  environments where tablespaces files are not moved.  Disabling tablespace path validation improves startup time  on systems with a large number of tablespace files. 

 ​  For more information, see  [Section 15.6.3.7, “Disabling Tablespace Path Validation”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-disabling-tablespace-path-validation). 

-  As of MySQL 8.0.21, on storage engines that support atomic  DDL, the  [`CREATE TABLE ... SELECT`](sql-statements.html#create-table-select) statement is logged as one  transaction in the binary log when row-based replication is  in use. Previously, it was logged as two transactions, one  to create the table, and the other to insert data. With this  change,  [`CREATE TABLE ... SELECT`](sql-statements.html#create-table-select) statements are now safe for  row-based replication and permitted for use with GTID-based  replication. For more information, see  [Section 13.1.1, “Atomic Data Definition Statement Support”](sql-statements.html#atomic-ddl). 

-  Truncating an undo tablespace on a busy system could affect  performance due to associated flushing operations that  remove old undo tablespace pages from the buffer pool and  flush the initial pages of the new undo tablespace to disk.  To address this issue, the flushing operations are removed  as of MySQL 8.0.21. 

 ​  Old undo tablespace pages are released passively as they  become least recently used, or are removed at the next full  checkpoint. The initial pages of the new undo tablespace are  now redo logged instead of flushed to disk during the  truncate operation, which also improves durability of the  undo tablespace truncate operation. 

 ​  To prevent potential issues caused by an excessive number of  undo tablespace truncate operations, truncate operations on  the same undo tablespace between checkpoints are now limited  to 64. If the limit is exceeded, an undo tablespace can  still be made inactive, but it is not truncated until after  the next checkpoint. 

 ​  [`INNODB_METRICS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-metrics-table) counters  associated with defunct undo truncate flushing operations  were removed. Removed counters include:  `undo_truncate_sweep_count`,  `undo_truncate_sweep_usec`,  `undo_truncate_flush_count`, and  `undo_truncate_flush_usec`. 

 ​  See [Section 15.6.3.4, “Undo Tablespaces”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-undo-tablespaces). 

- **Character set support.** The default character set has changed from `latin1` to `utf8mb4`. The `utf8mb4` character set has several new collations, including `utf8mb4_ja_0900_as_cs`, the first Japanese language-specific collation available for Unicode in MySQL. For more information, see [Section 10.10.1, “Unicode Character Sets”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/charset.html#charset-unicode-sets).  

 

 

- **JSON enhancements.** The following enhancements or additions were made to MySQL's JSON functionality:

 

 

 - Added the [`->>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_json-inline-path) (inline path) operator, which is equivalent to calling [`JSON_UNQUOTE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-unquote) on the result of [`JSON_EXTRACT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-extract). 

 ​ This is a refinement of the column path operator [`->`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_json-column-path) introduced in MySQL 5.7; `col->>"$.path"` is equivalent to `JSON_UNQUOTE(col->"$.path")`. The inline path operator can be used wherever you can use `JSON_UNQUOTE(JSON_EXTRACT())`, such [`SELECT`](sql-statements.html#select) column lists, `WHERE` and `HAVING` clauses, and `ORDER BY` and `GROUP BY` clauses. For more information, see the description of the operator, as well as [JSON Path Syntax](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json-path-syntax). 

 - Added two JSON aggregation functions [`JSON_ARRAYAGG()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-arrayagg) and [`JSON_OBJECTAGG()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-objectagg). `JSON_ARRAYAGG()` takes a column or expression as its argument, and aggregates the result as a single [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) array. The expression can evaluate to any MySQL data type; this does not have to be a `JSON` value. `JSON_OBJECTAGG()` takes two columns or expressions which it interprets as a key and a value; it returns the result as a single `JSON` object. For more information and examples, see [Section 12.20, “Aggregate Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#aggregate-functions-and-modifiers). 

 - Added the JSON utility function [`JSON_PRETTY()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-pretty), which outputs an existing [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) value in an easy-to-read format; each JSON object member or array value is printed on a separate line, and a child object or array is intended 2 spaces with respect to its parent. 

 ​ This function also works with a string that can be parsed as a JSON value. 

 ​ For more detailed information and examples, see [Section 12.17.8, “JSON Utility Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-utility-functions). 

 - When sorting [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) values in a query using `ORDER BY`, each value is now represented by a variable-length part of the sort key, rather than a part of a fixed 1K in size. In many cases this can reduce excessive usage. For example, a scalar `INT` or even `BIGINT` value actually requires very few bytes, so that the remainder of this space (up to 90% or more) was taken up by padding. This change has the following benefits for performance:

 - Sort buffer space is now used more effectively, so that filesorts need not flush to disk as early or often as with fixed-length sort keys. This means that more data can be sorted in memory, avoiding unnecessary disk access. 
 - Shorter keys can be compared more quickly than longer ones, providing a noticeable improvement in performance. This is true for sorts performed entirely in memory as well as for sorts that require writing to and reading from disk.

 - Added support in MySQL 8.0.2 for partial, in-place updates of `JSON` column values, which is more efficient than completely removing an existing JSON value and writing a new one in its place, as was done previously when updating any `JSON` column. For this optimization to be applied, the update must be applied using [`JSON_SET()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-set), [`JSON_REPLACE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-replace), or [`JSON_REMOVE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-remove). New elements cannot be added to the JSON document being updated; values within the document cannot take more space than they did before the update. See [Partial Updates of JSON Values](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json-partial-updates), for a detailed discussion of the requirements. 

 ​ Partial updates of JSON documents can be written to the binary log, taking up less space than logging complete JSON documents. Partial updates are always logged as such when statement-based replication is in use. For this to work with row-based replication, you must first set [`binlog_row_value_options=PARTIAL_JSON`](replication#sysvar_binlog_row_value_options); see this variable's description for more information. 

 - Added the JSON utility functions [`JSON_STORAGE_SIZE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-storage-size) and [`JSON_STORAGE_FREE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-storage-free). `JSON_STORAGE_SIZE()` returns the storage space in bytes used for the binary representation of a JSON document prior to any partial update (see previous item). `JSON_STORAGE_FREE()` shows the amount of space remaining in a table column of type [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) after it has been partially updated using `JSON_SET()` or `JSON_REPLACE()`; this is greater than zero if the binary representation of the new value is less than that of the previous value. 

 ​ Each of these functions also accepts a valid string representation of a JSON document. For such a value, `JSON_STORAGE_SIZE()` returns the space used by its binary representation following its conversion to a JSON document. For a variable containing the string representation of a JSON document, `JSON_STORAGE_FREE()` returns zero. Either function produces an error if its (non-null) argument cannot be parsed as a valid JSON document, and `NULL` if the argument is `NULL`. 

 ​ For more information and examples, see [Section 12.17.8, “JSON Utility Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-utility-functions). 

 ​ `JSON_STORAGE_SIZE()` and `JSON_STORAGE_FREE()` were implemented in MySQL 8.0.2. 

 - Added support in MySQL 8.0.2 for ranges such as `$[1 to 5]` in XPath expressions. Also added support in this version for the `last` keyword and relative addressing, such that `$[last]` always selects the last (highest-numbered) element in the array and `$[last-1]` the next to last element. `last` and expressions using it can also be included in range definitions. For example, `$[last-2 to last-1]` returns the last two elements but one from an array. See [Searching and Modifying JSON Values](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json-paths), for additional information and examples. 

 - Added a JSON merge function intended to conform to [RFC 7396](https://tools.ietf.org/html/rfc7396). [`JSON_MERGE_PATCH()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge-patch), when used on 2 JSON objects, merges them into a single JSON object that has as members a union of the following sets:

 - Each member of the first object for which there is no member with the same key in the second object. 
 - Each member of the second object for which there is no member having the same key in the first object, and whose value is not the JSON `null` literal. 
 - Each member having a key that exists in both objects, and whose value in the second object is not the JSON `null` literal.

 ​ As part of this work, the [`JSON_MERGE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge) function has been renamed [`JSON_MERGE_PRESERVE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge-preserve). `JSON_MERGE()` continues to be recognized as an alias for `JSON_MERGE_PRESERVE()` in MySQL 8.0, but is now deprecated and is subject to removal in a future version of MySQL. 

 ​ For more information and examples, see [Section 12.17.4, “Functions That Modify JSON Values”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-modification-functions). 

 - Implemented “last duplicate key wins” normalization of duplicate keys, consistent with [RFC 7159](https://tools.ietf.org/html/rfc7159) and most JavaScript parsers. An example of this behavior is shown here, where only the rightmost member having the key `x` is preserved: 

 ```
 mysql> SELECT JSON_OBJECT('x', '32', 'y', '[true, false]',
 > 'x', '"abc"', 'x', '100') AS Result;
 +------------------------------------+
 | Result |
 +------------------------------------+
 | {"x": "100", "y": "[true, false]"} |
 +------------------------------------+
 1 row in set (0.00 sec)
 ```

 ​ Values inserted into MySQL [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) columns are also normalized in this way, as shown in this example: 

 ```
 mysql> CREATE TABLE t1 (c1 JSON);
 
 mysql> INSERT INTO t1 VALUES ('{"x": 17, "x": "red", "x": [3, 5, 7]}');
 
 mysql> SELECT c1 FROM t1;
 +------------------+
 | c1 |
 +------------------+
 | {"x": [3, 5, 7]} |
 +------------------+
 ```

 ​ This is an incompatible change from previous versions of MySQL, where a “first duplicate key wins” algorithm was used in such cases. 

 ​ See [Normalization, Merging, and Autowrapping of JSON Values](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json-normalization), for more information and examples. 

 - Added the [`JSON_TABLE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-table) function in MySQL 8.0.4. This function accepts JSON data and returns it as a relational table having the specified columns. 

 ​ This function has the syntax `JSON_TABLE(*`expr`*, *`path`* COLUMNS *`column_list`*) [AS] *`alias`*)`, where *`expr`* is an expression that returns JSON data, *`path`* is a JSON path applied to the source, and *`column_list`* is a list of column definitions. An example is shown here: 

 ```
 mysql> SELECT *
 -> FROM
 -> JSON_TABLE(
 ->  '[{"a":3,"b":"0"},{"a":"3","b":"1"},{"a":2,"b":1},{"a":0},{"b":[1,2]}]',
 ->  "$[*]" COLUMNS(
 -> rowid FOR ORDINALITY,
 ->
 -> xa INT EXISTS PATH "$.a",
 -> xb INT EXISTS PATH "$.b",
 ->
 -> sa VARCHAR(100) PATH "$.a",
 -> sb VARCHAR(100) PATH "$.b",
 ->
 -> ja JSON PATH "$.a",
 -> jb JSON PATH "$.b"
 ->  )
 -> ) AS jt1;
 +-------+------+------+------+------+------+--------+
 | rowid | xa | xb | sa | sb | ja | jb  |
 +-------+------+------+------+------+------+--------+
 |  1 | 1 | 1 | 3 | 0 | 3 | "0" |
 |  2 | 1 | 1 | 3 | 1 | "3" | "1" |
 |  3 | 1 | 1 | 2 | 1 | 2 | 1 |
 |  4 | 1 | 0 | 0 | NULL | 0 | NULL |
 |  5 | 0 | 1 | NULL | NULL | NULL | [1, 2] |
 +-------+------+------+------+------+------+--------+
 ```

 ​ The JSON source expression can be any expression that yields a valid JSON document, including a JSON literal, a table column, or a function call that returns JSON such as [`JSON_EXTRACT(t1, data, '$.post.comments')`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-extract). For more information, see [Section 12.17.6, “JSON Table Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-table-functions).

- **Data type support.** MySQL now supports use of expressions as default values in data type specifications. This includes the use of expressions as default values for the [`BLOB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob), [`TEXT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob), `GEOMETRY`, and [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) data types, which previously could not be assigned default values at all. For details, see [Section 11.6, “Data Type Default Values”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#data-type-defaults).  

 

 

- **Optimizer.** These optimizer enhancements were added:

 

 

 - MySQL now supports invisible indexes. An invisible index is not used by the optimizer at all, but is otherwise maintained normally. Indexes are visible by default. Invisible indexes make it possible to test the effect of removing an index on query performance, without making a destructive change that must be undone should the index turn out to be required. See [Section 8.3.12, “Invisible Indexes”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#invisible-indexes). 

 - MySQL now supports descending indexes: `DESC` in an index definition is no longer ignored but causes storage of key values in descending order. Previously, indexes could be scanned in reverse order but at a performance penalty. A descending index can be scanned in forward order, which is more efficient. Descending indexes also make it possible for the optimizer to use multiple-column indexes when the most efficient scan order mixes ascending order for some columns and descending order for others. See [Section 8.3.13, “Descending Indexes”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#descending-indexes). 

 - MySQL now supports creation of functional index key parts that index expression values rather than column values. Functional key parts enable indexing of values that cannot be indexed otherwise, such as [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) values. For details, see [Section 13.1.15, “CREATE INDEX Statement”](sql-statements.html#create-index). 

 - In MySQL 8.0.14 and later, trivial `WHERE` conditions arising from constant literal expressions are removed during preparation, rather than later on during optimization. Removal of the condition earlier in the process makes it possible to simplify joins for queries with outer joins having trivial conditions, such as this one: 

 ```
 SELECT * FROM t1 LEFT JOIN t2 ON condition_1 WHERE condition_2 OR 0 = 1
 ```

 ​ The optimizer now sees during preparation that 0 = 1 is always false, making `OR 0 = 1` redundant, and removes it, leaving this: 

 ```
 SELECT * FROM t1 LEFT JOIN t2 ON condition_1 where condition_2
 ```

 ​ Now the optimizer can rewrite the query as an inner join, like this: 

 ```
 SELECT * FROM t1 LEFT JOIN t2 WHERE condition_1 AND condition_2
 ```

 ​ For more information, see [Section 8.2.1.9, “Outer Join Optimization”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#outer-join-optimization). 

 - In MySQL 8.0.16 and later, MySQL can use constant folding at optimization time to handle comparisons between a column and a constant value where the constant is out of range or on a range boundary with respect to the type of the column, rather than doing so for each row at execution time. For example, given a table `t` with a `TINYINT UNSIGNED` column `c`, the optimizer can rewrite a condition such as `WHERE c < 256` to `WHERE 1` (and optimize the condition away altogether), or `WHERE c >= 255` to `WHERE c = 255`. 

 ​ See [Section 8.2.1.14, “Constant-Folding Optimization”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#constant-folding-optimization), for more information. 

 - Beginning with MySQL 8.0.16, the semijoin optimizations used with `IN` subqueries can now be applied to `EXISTS` subqueries as well. In addition, the optimizer now decorrelates trivially-correlated equality predicates in the `WHERE` condition attached to the subquery, so that they can be treated similarly to expressions in `IN` subqueries; this applies to both `EXISTS` and `IN` subqueries. 

 ​ For more information, see [Section 8.2.2.1, “Optimizing IN and EXISTS Subquery Predicates with Semijoin Transformations”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#semijoins). 

 - As of MySQL 8.0.17, the server rewrites any incomplete SQL predicates (that is, predicates having the form `WHERE *`value`*`, in which *`value`* is a column name or constant expression and no comparison operator is used) internally as `WHERE *`value`* <> 0` during the contextualization phase, so that the query resolver, query optimizer, and query executor need work only with complete predicates. 

 ​ One visible effect of this change is that, for Boolean values, [`EXPLAIN`](sql-statements.html#explain) output now shows `true` and `false`, rather than `1` and `0`. 

 ​ Another effect of this change is that evaluation of a JSON value in an SQL boolean context performs an implicit comparison against JSON integer 0. Consider the table created and populated as shown here: 

 ```
 mysql> CREATE TABLE test (id INT, col JSON);
 
 mysql> INSERT INTO test VALUES (1, '{"val":true}'), (2, '{"val":false}');
 ```

 ​ Previously, the server attempted to convert an extracted `true` or `false` value to an SQL boolean when comparing it in an SQL boolean context, as shown by the following query using `IS TRUE`: 

 ```
 mysql> SELECT id, col, col->"$.val" FROM test WHERE col->"$.val" IS TRUE;
 +------+---------------+--------------+
 | id | col | col->"$.val" |
 +------+---------------+--------------+
 | 1 | {"val": true} | true |
 +------+---------------+--------------+
 ```

 ​ In MySQL 8.0.17 and later, the implicit copmparison of the extracted value with JSON integer 0 leads to a different result: 

 ```
 mysql> SELECT id, col, col->"$.val" FROM test WHERE col->"$.val" IS TRUE;
 +------+----------------+--------------+
 | id | col  | col->"$.val" |
 +------+----------------+--------------+
 | 1 | {"val": true} | true |
 | 2 | {"val": false} | false |
 +------+----------------+--------------+
 ```

 ​ Beginning with MySQL 8.0.21, you can use [`JSON_VALUE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-value) on the extracted value to perform type conversion prior to performing the test, as shown here: 

 ```
 mysql> SELECT id, col, col->"$.val" FROM test
 ->  WHERE JSON_VALUE(col, "$.val" RETURNING UNSIGNED) IS TRUE;
 +------+---------------+--------------+
 | id | col | col->"$.val" |
 +------+---------------+--------------+
 | 1 | {"val": true} | true |
 +------+---------------+--------------+
 ```

 ​ Also beginning with MySQL 8.0.21, the server provides the warning Evaluating a JSON value in SQL boolean context does an implicit comparison against JSON integer 0; if this is not what you want, consider converting JSON to a SQL numeric type with JSON_VALUE RETURNING when comparing extracted values in an SQL boolean context in this manner. 

 - In MySQL 8.0.17 and later a `WHERE` condition having `NOT IN (*`subquery`*)` or `NOT EXISTS (*`subquery`*)` is transformed internally into an antijoin. (An antijoin returns all rows from the table for which there is no row in the table to which it is joined matching the join condition.) This removes the subquery which can result in faster query execution since the subquery's tables are now handled on the top level. 

 ​ This is similar to, and reuses, the existing `IS NULL` (`Not exists`) optimization for outer joins; see [EXPLAIN Extra Information](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#explain-extra-information). 

 - Beginning with MySQL 8.0.21, a single-table [`UPDATE`](sql-statements.html#update) or [`DELETE`](sql-statements.html#delete) statement can now in many cases make use of a semijoin transformation or subquery materialization. This applies to statements of the forms shown here:

 - `UPDATE t1 SET t1.a=*`value`* WHERE t1.a IN (SELECT t2.a FROM t2)` 
 - `DELETE FROM t1 WHERE t1.a IN (SELECT t2.a FROM t2)`

 ​ This can be done for a single-table `UPDATE` or `DELETE` meeting the following conditions:

 - The `UPDATE` or `DELETE` statement uses a subquery having a `[NOT] IN` or `[NOT] EXISTS` predicate. 

 - The statement has no `ORDER BY` clause, and has no `LIMIT` clause. 

 ​ (The multi-table versions of `UPDATE` and `DELETE` do not support `ORDER BY` or `LIMIT`.) 

 - The target table does not support read-before-write removal (relevant only for [`NDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html) tables). 

 - Semijoin or subquery materialization is allowed, based on any hints contained in the subquery and the value of [`optimizer_switch`](server-administration#sysvar_optimizer_switch).

 ​ When the semijoin optimization is used for an eligible single-table `DELETE` or `UPDATE`, this is visible in the optimizer trace: for a multi-table statement there is a `join_optimization` object in the trace, while there is none for a single-table statement. The conversion is also visible in the output of `EXPLAIN FORMAT=TREE` or [`EXPLAIN ANALYZE`](sql-statements.html#explain-analyze); a single-table statement shows `<not executable by iterator executor>`, while a multi-table statement reports a full plan. 

 ​ Alo beginning with MySQL 8.0.21, semi-consistent reads are supported by multi-table `UPDATE` statements using [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) tables, for transaction isolation levels weaker than [`REPEATABLE READ`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#isolevel_repeatable-read).

- **Common table expressions.** MySQL now supports common table expressions, both nonrecursive and recursive. Common table expressions enable use of named temporary result sets, implemented by permitting a [`WITH`](sql-statements.html#with) clause preceding [`SELECT`](sql-statements.html#select) statements and certain other statements. For more information, see [Section 13.2.15, “WITH (Common Table Expressions)”](sql-statements.html#with).  

 

 

 ​  As of MySQL 8.0.19, the recursive  [`SELECT`](sql-statements.html#select) part of a recursive  common table expression (CTE) supports a  `LIMIT` clause. `LIMIT`  with `OFFSET` is also supported. See  [Recursive Common Table Expressions](sql-statements.html#common-table-expressions-recursive), for  more information. 

- **Window functions.** MySQL now supports window functions that, for each row from a query, perform a calculation using rows related to that row. These include functions such as [`RANK()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_rank), [`LAG()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_lag), and [`NTILE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_ntile). In addition, several existing aggregate functions now can be used as window functions (for example, [`SUM()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_sum) and [`AVG()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_avg)). For more information, see [Section 12.21, “Window Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#window-functions).  

 

 

- **Lateral derived tables.** A derived table now may be preceded by the `LATERAL` keyword to specify that it is permitted to refer to (depend on) columns of preceding tables in the same `FROM` clause. Lateral derived tables make possible certain SQL operations that cannot be done with nonlateral derived tables or that require less-efficient workarounds. See [Section 13.2.11.9, “Lateral Derived Tables”](sql-statements.html#lateral-derived-tables).  

 

 

- **Aliases in single-table DELETE statements.** In MySQL 8.0.16 and later, single-table [`DELETE`](sql-statements.html#delete) statements support the use of table aliases.  

 

 

- **Regular expression support.** Previously, MySQL used the Henry Spencer regular expression library to support regular expression operators ([`REGEXP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_regexp), [`RLIKE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_regexp)). Regular expression support has been reimplemented using International Components for Unicode (ICU), which provides full Unicode support and is multibyte safe. The [`REGEXP_LIKE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_regexp-like) function performs regular expression matching in the manner of the [`REGEXP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_regexp) and [`RLIKE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_regexp) operators, which now are synonyms for that function. In addition, the [`REGEXP_INSTR()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_regexp-instr), [`REGEXP_REPLACE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_regexp-replace), and [`REGEXP_SUBSTR()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_regexp-substr) functions are available to find match positions and perform substring substitution and extraction, respectively. The [`regexp_stack_limit`](server-administration#sysvar_regexp_stack_limit) and [`regexp_time_limit`](server-administration#sysvar_regexp_time_limit) system variables provide control over resource consumption by the match engine. For more information, see [Section 12.7.2, “Regular Expressions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#regexp). For information about ways in which applications that use regular expressions may be affected by the implementation change, see [Regular Expression Compatibility Considerations](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#regexp-compatibility).  

 

 

- **Internal temporary tables.** The `TempTable` storage engine replaces the `MEMORY` storage engine as the default engine for in-memory internal temporary tables. The `TempTable` storage engine provides efficient storage for [`VARCHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char) and [`VARBINARY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#binary-varbinary) columns. The [`internal_tmp_mem_storage_engine`](server-administration#sysvar_internal_tmp_mem_storage_engine) session variable defines the storage engine for in-memory internal temporary tables. Permitted values are `TempTable` (the default) and `MEMORY`. The [`temptable_max_ram`](server-administration#sysvar_temptable_max_ram) variable defines the maximum amount of memory that the `TempTable` storage engine can use before data is stored to disk.  

 

 

- **Logging.** Error logging was rewritten to use the MySQL component architecture. Traditional error logging is implemented using built-in components, and logging using the system log is implemented as a loadable component. In addition, a loadable JSON log writer is available. To control which log components to enable, use the [`log_error_services`](server-administration#sysvar_log_error_services) system variable. For more information, see [Section 5.4.2, “The Error Log”](server-administration#error-log).  

 

 

- **Backup lock.** A new type of backup lock permits DML during an online backup while preventing operations that could result in an inconsistent snapshot. The new backup lock is supported by [`LOCK INSTANCE FOR BACKUP`](sql-statements.html#lock-instance-for-backup) and [`UNLOCK INSTANCE`](sql-statements.html#lock-instance-for-backup) syntax. The [`BACKUP_ADMIN`](security#priv_backup-admin) privilege is required to use these statements.  

 

 

- **Replication.** The following enhancements have been made to MySQL Replication:

 

 

 - MySQL Replication now supports binary logging of partial updates to JSON documents using a compact binary format, saving space in the log over logging complete JSON documents. Such compact logging is done automatically when statement-based logging is in use, and can be enabled by setting the new `binlog_row_value_options` system variable to `PARTIAL_JSON`. For more information, see [Partial Updates of JSON Values](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json-partial-updates), as well as the description of [`binlog_row_value_options`](replication#sysvar_binlog_row_value_options).

- **Connection management.** MySQL Server now permits a TCP/IP port to be configured specifically for administrative connections. This provides an alternative to the single administrative connection that is permitted on the network interfaces used for ordinary connections even when [`max_connections`](server-administration#sysvar_max_connections) connections are already established. See [Section 5.1.12.1, “Connection Interfaces”](server-administration#connection-interfaces).  

 

 

 ​  MySQL now provides more control over the use of compression  to minimize the number of bytes sent over connections to the  server. Previously, a given connection was either  uncompressed or used the `zlib` compression  algorithm. Now, it is also possible to use the  `zstd` algorithm, and to select a  compression level for `zstd` connections.  The permitted compression algorithms can be configured on  the server side, as well as on the connection-origination  side for connections by client programs and by servers  participating in master/slave replication or Group  Replication. For more information, see  [Section 4.2.8, “Connection Compression Control”](programs#connection-compression-control). 

- **Configuration.** The maximum permitted length of host names throughout MySQL has been raised to 255 ASCII characters, up from the previous limit of 60 characters. This applies to, for example, host name-related columns in the data dictionary, `mysql` system schema, Performance Schema, `INFORMATION_SCHEMA`, and `sys` schema; the `MASTER_HOST` value for the [`CHANGE MASTER TO`](sql-statements.html#change-master-to) statement; the `Host` column in [`SHOW PROCESSLIST`](sql-statements.html#show-processlist) statement output; host names in account names (such as used in account-management statements and in `DEFINER` attributes); and host name-related command options and system variables.  

 

 

 

 ​  Caveats:

 - The increase in permitted host name length can affect tables with indexes on host name columns. For example, tables in the `mysql` system schema that index host names now have an explicit `ROW_FORMAT` attribute of `DYNAMIC` to accommodate longer index values. 
 - Some file name-valued configuration settings might be constructed based on the server host name. The permitted values are constrained by the underlying operating system, which may not permit file names long enough to include 255-character host names. This affects the [`general_log_file`](server-administration#sysvar_general_log_file), [`log_error`](server-administration#sysvar_log_error), [`pid_file`](server-administration#sysvar_pid_file), [`relay_log`](replication#sysvar_relay_log), and [`slow_query_log_file`](server-administration#sysvar_slow_query_log_file) system variables and corresponding options. If host name-based values are too long for the OS, explicit shorter values must be provided. 
 - Although the server now supports 255-character host names, connections to the server established using the [`--ssl-mode=VERIFY_IDENTITY`](programs#option_general_ssl-mode) option are constrained by maximum host name length supported by OpenSSL. Host name matches pertain to two fields of SSL certificates, which have maximum lengths as follows: Common Name: maximum length 64; Subject Alternative Name: maximum length as per RFC#1034.

- **Plugins.** Previously, MySQL plugins could be written in C or C++. MySQL header files used by plugins now contain C++ code, which means that plugins must be written in C++, not C.  

 

 

- **C API.** The MySQL C API now supports asynchronous functions for nonblocking communication with the MySQL server. Each function is the asynchronous counterpart to an existing synchronous function. The synchronous functions block if reads from or writes to the server connection must wait. The asynchronous functions enable an application to check whether work on the server connection is ready to proceed. If not, the application can perform other work before checking again later. See [C API Asynchronous Interface](https://dev.mysql.com/doc/c-api/8.0/en/c-api-asynchronous-interface.html).  

 

 

- **Additional target types for casts.** The functions [`CAST()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_cast) and [`CONVERT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_convert) now support conversions to types [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types), [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types), and [`REAL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types). Added in MySQL 8.0.17. See [Section 12.10, “Cast Functions and Operators”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#cast-functions).  

 

 

- **JSON schema validation.** MySQL 8.0.17 adds two functions [`JSON_SCHEMA_VALID()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-schema-valid) and [`JSON_SCHEMA_VALIDATION_REPORT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-schema-validation-report) for validating JSON documents again JSON schemas. `JSON_SCHEMA_VALID()` returns TRUE (1) if the document validates against the schema and FALSE (0) if it does not. `JSON_SCHEMA_VALIDATION_REPORT()` returns a JSON document containing detailed information about the results of the validation. The following statements apply to both of these functions:

 

 

 - The schema must conform to Draft 4 of the JSON Schema specification. 
 - `required` attributes are supported. 
 - External resources and the `$ref` keyword are not supported. 
 - Regular expression patterns are supported; invalid patterns are silently ignored.

 ​  See [Section 12.17.7, “JSON Schema Validation Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-validation-functions), for more  information and examples. 

- **Multi-valued indexes.** Beginning with MySQL 8.0.17, [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) supports the creation of a multi-valued index, which is a secondary index defined on a [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) column that stores an array of values and which can have multiple index records for a single data record. Such an index uses a key part definition such as `CAST(data->'$.zipcode' AS UNSIGNED ARRAY)`. A multi-valued index is used automatically by the MySQL optimizer for suitable queries, as can be viewed in the output of [`EXPLAIN`](sql-statements.html#explain).  

 

 

 ​  As part of this work, MySQL adds a new function  [`JSON_OVERLAPS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-overlaps) and a new  [`MEMBER OF()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_member-of) operator for  working with [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) documents,  additionally extending the  [`CAST()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_cast) function with a new  `ARRAY` keyword, as described in the  following list:

 - `JSON_OVERLAPS()` compares two [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) documents. If they contain any key-value pairs or array elements in common, the function returns TRUE (1); otherwise it returns FALSE (0). If both values are scalars, the function performs a simple test for equality. If one argument is a JSON array and the other is a scalar, the scalar is treated as an array element. Thus, `JSON_OVERLAPS()` acts as a complement to [`JSON_CONTAINS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-contains). 
 - `MEMBER OF()` tests whether the first operand (a scalar or JSON document) is a member of the JSON array passed as the second operand, returning TRUE (1) if it is, and FALSE (0) if it is not. No type conversion of the operand is performed. 
 - `CAST(expression AS type ARRAY)` permits creation of a functional index by casting the JSON array found in a JSON document at *`json_path`* to an SQL array. Type specifiers are limited to those already supported by `CAST()`, with the exception of `BINARY` (not supported). This usage of `CAST()` (and the `ARRAY` keyword) is supported only by [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html), and only for the creation of a multi-valued index.

 ​  For detailed information about multi-valued indexes,  including examples, see  [Multi-Valued Indexes](sql-statements.html#create-index-multi-valued).  [Section 12.17.3, “Functions That Search JSON Values”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-search-functions), provides  information about `JSON_OVERLAPS()` and  `MEMBER OF()`, along with examples of use. 

- **Hintable time_zone.** As of MySQL 8.0.17, the [`time_zone`](server-administration#sysvar_time_zone) session variable is hintable using [`SET_VAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-set-var).  

 

 

- **Redo Log Archiving.** As of MySQL 8.0.17, `InnoDB` supports redo log archiving. Backup utilities that copy redo log records may sometimes fail to keep pace with redo log generation while a backup operation is in progress, resulting in lost redo log records due to those records being overwritten. The redo log archiving feature addresses this issue by sequentially writing redo log records to an archive file. Backup utilities can copy redo log records from the archive file as necessary, thereby avoiding the potential loss of data. For more information, see [Redo Log Archiving](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-redo-log-archiving).  

 

 

- **The Clone Plugin.** As of MySQL 8.0.17, MySQL provides a clone plugin that permits cloning `InnoDB` data locally or from a remote MySQL server instance. A local cloning operation stores cloned data on the same server or node where the MySQL instance runs. A remote cloning operation transfers cloned data over the network from a donor MySQL server instance to the recipient server or node where the cloning operation was initiated.  

 

 

 ​  The clone plugin supports replication. In addition to  cloning data, a cloning operation extracts and transfers  replication coordinates from the donor and applies them on  the recipient, which enables using the clone plugin for  provisioning Group Replication members and replication  slaves. Using the clone plugin for provisioning is  considerably faster and more efficient than replicating a  large number of transactions. Group Replication members can  also be configured to use the clone plugin as an alternative  method of recovery, so that members automatically choose the  most efficient way to retrieve group data from seed members. 

 ​  For more information, see [Section 5.6.7, “The Clone Plugin”](server-administration#clone-plugin),  and [Section 18.4.3.2, “Cloning for Distributed Recovery”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/group-replication.html#group-replication-cloning). 

- **Hash Join Optimization.** Beginning with MySQL 8.0.18, a hash join is used whenever each pair of tables in a join includes at least one equi-join condition. A hash join does not require indexes, and is more efficient in most cases than the block-nested loop algorithm. Joins such as those shown here can be optimized in this manner:  

 

 

 ```
 SELECT *
 FROM t1
 JOIN t2
 ON t1.c1=t2.c1;
 
 SELECT *
 FROM t1
 JOIN t2
 ON (t1.c1 = t2.c1 AND t1.c2 < t2.c2)
 JOIN t3
 ON (t2.c1 = t3.c1)
 ```

 ​  Hash joins can also be used for Cartesian  products—that is, when no join condition is specified. 

 ​  You can see when the hash join optimization is being used  for a particular query using  [`EXPLAIN FORMAT=TREE`](sql-statements.html#explain) or [`EXPLAIN ANALYZE`](sql-statements.html#explain-analyze). (In MySQL 8.0.20 and later, you can also  use `EXPLAIN`, omitting  `FORMAT=TREE`.) 

 ​  The amount of memory available to a hash join is limited by  the value of  [`join_buffer_size`](server-administration#sysvar_join_buffer_size). A hash  join that requires more than this much memory is executed on  disk; the number of disk files that can be used by an  on-disk hash join is limited by  [`open_files_limit`](server-administration#sysvar_open_files_limit). 

 ​  As of MySQL 8.0.19, the `hash_join`  optimizer switch which was introduced in MySQL 8.0.18 no  longer supported (hash_join=on still appears as part of the  value of optimizer_switch, but setting it no longer has any  effect). The [`HASH_JOIN`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-table-level) and  `NO_HASH_JOIN` optimizer hints are also no  longer supported. The switch and the hint are both now  deprecated and will be removed in a future MySQL release. In  MySQL 8.0.18 and later, hash joins can be disabled using the  [`NO_BNL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-table-level) optimizer switch. 

 ​  In MySQL 8.0.20, block nested loop is no longer used in the  MySQL server, and a hash join is employed any time a block  nested loop would have been used previously, even when the  query contains no equi-join conditions. This applies to  inner non-equi-joins, semijoins, antijoins, left outer  joins, and right outer joins. This also means that the  `block_nested_loop` flag for the  [`optimizer_switch`](server-administration#sysvar_optimizer_switch) system  variable no longer has any effect; the  [`BNL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-table-level) and  `NO_BNL` optimizer hints are still  supported for controlling use of hash joins. In addition,  both inner and outer joins (including semijoins and  antijoins) can now employ batched key access (BKA), which  allocates join buffer memory incrementally so that  individual queries need not use up large amounts of  resources that they do not actually require for resolution.  BKA for inner joins only is supported starting with MySQL  8.0.18. 

 ​  MySQL 8.0.20 also replaces the executor used in previous  versions of MySQL with the iterator executor. This work  includes replacement of the old index subquery engines that  governed queries of the form `WHERE  *`value`* IN (SELECT  *`column`* FROM  *`table`* WHERE ...)` for  those `IN` queries which have not been  optimized as semijoins, as well as queries materialized in  the same form, which formerly depended on the old executor. 

 ​  For more information and examples, see  [Section 8.2.1.4, “Hash Join Optimization”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#hash-joins). See also  [Batched Key Access Joins](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#bka-optimization). 

- **EXPLAIN ANALYZE Statement.** A new form of the [`EXPLAIN`](sql-statements.html#explain) statement, [`EXPLAIN ANALYZE`](sql-statements.html#explain-analyze), is implemented in MySQL 8.0.18, providing expanded information about the execution of [`SELECT`](sql-statements.html#select) statements in `TREE` format for each iterator used in processing the query, and making it possible to compare estimated cost with the actual cost of the query. This information includes startup cost, total cost, number of rows returned by this iterator, and the number of loops executed.  

 ​  In MySQL 8.0.21 and later, this statement also supports a  `FORMAT=TREE` specifier.  `TREE` is the only supported format. 

 

 

 ​  See [Obtaining Information with EXPLAIN ANALYZE](sql-statements.html#explain-analyze), for more information. 

- **Query cast injection.** In version 8.0.18 and later, MySQL injects cast operations into the query item tree inside expressions and conditions in which the data type of the argument and the expected data type do not match. This has no effect on query results or speed of execution, but makes the query as executed equivalent to one which is compliant with the SQL standard while maintaining backwards compatibility with previous releases of MySQL.  

 

 

 ​  Such implicit casts are now performed between temporal types  ([`DATE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime),  [`DATETIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime),  [`TIMESTAMP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime),  [`TIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#time)) and numeric types  ([`SMALLINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types),  [`TINYINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types),  [`MEDIUMINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types),  [`INT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types)/[`INTEGER`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types),  [`BIGINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types);  [`DECIMAL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#fixed-point-types)/[`NUMERIC`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#fixed-point-types);  [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types),  [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types),  [`REAL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types);  [`BIT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#bit-type)) whenever they are  compared using any of the standard numeric comparison  operators  ([`=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_assign-equal),  [`>=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_greater-than-or-equal),  [`>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_greater-than),  [`<`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_less-than),  [`<=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_less-than-or-equal),  [`<>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not-equal)/[`!=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not-equal),  or  [`<=>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_equal-to)).  In this case, any value that is not already a  `DOUBLE` is cast as one. Cast injection is  also now performed for comparisons between  [`DATE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime) or  [`TIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#time) values and  [`DATETIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime) values, where the  arguments are cast whenever necessary as  `DATETIME`. 

 ​  Beginning with MySQL 8.0.21, such casts are also performed  when comparing string types with other types. String types  that are cast include [`CHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char),  [`VARCHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char),  [`BINARY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#binary-varbinary),  [`VARBINARY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#binary-varbinary),  [`BLOB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob),  [`TEXT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob),  [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum), and  [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set). When comparing a value  of a string type with a numeric type or  `YEAR`, the string cast is to  `DOUBLE`; if the type of the other argument  is not `FLOAT`, `DOUBLE`,  or `REAL`, it is also cast to  `DOUBLE`. When comparing a string type to a  `DATETIME` or `TIMESTAMP`  value, the string is cast is to `DATETIME`;  when comparing a string type with `DATE`,  the string is cast to `DATE`. 

 ​  It is possible to see when casts are injected into a given  query by viewing the output of [`EXPLAIN ANALYZE`](sql-statements.html#explain-analyze), `EXPLAIN FORMAT=JSON`,  or, as shown here, `EXPLAIN FORMAT=TREE`: 

 ```
 mysql> CREATE TABLE d (dt DATETIME, d DATE, t TIME);
 Query OK, 0 rows affected (0.62 sec)
 
 mysql> CREATE TABLE n (i INT, d DECIMAL, f FLOAT, dc DECIMAL);
 Query OK, 0 rows affected (0.51 sec)
 
 mysql> CREATE TABLE s (c CHAR(25), vc VARCHAR(25),
 ->  bn BINARY(50), vb VARBINARY(50), b BLOB, t TEXT,
 ->  e ENUM('a', 'b', 'c'), se SET('x' ,'y', 'z'));
 Query OK, 0 rows affected (0.50 sec)
 
 mysql> EXPLAIN FORMAT=TREE SELECT * from d JOIN n ON d.dt = n.i\G
 *************************** 1. row ***************************
 EXPLAIN: -> Inner hash join (cast(d.dt as double) = cast(n.i as double))
 (cost=0.70 rows=1)
 -> Table scan on n (cost=0.35 rows=1)
 -> Hash
 -> Table scan on d (cost=0.35 rows=1)
 
 mysql> EXPLAIN FORMAT=TREE SELECT * from s JOIN d ON d.dt = s.c\G
 *************************** 1. row ***************************
 EXPLAIN: -> Inner hash join (d.dt = cast(s.c as datetime(6))) (cost=0.72 rows=1)
 -> Table scan on d (cost=0.37 rows=1)
 -> Hash
 -> Table scan on s (cost=0.35 rows=1)
 
 1 row in set (0.01 sec)
 
 mysql> EXPLAIN FORMAT=TREE SELECT * from n JOIN s ON n.d = s.c\G
 *************************** 1. row ***************************
 EXPLAIN: -> Inner hash join (cast(n.d as double) = cast(s.c as double)) (cost=0.70 rows=1)
 -> Table scan on s (cost=0.35 rows=1)
 -> Hash
 -> Table scan on n (cost=0.35 rows=1)
 
 1 row in set (0.00 sec)
 ```

 ​  Such casts can also be seen by executing `EXPLAIN  [FORMAT=TRADITIONAL]`, in which case it is also  necessary to issue [`SHOW WARNINGS`](sql-statements.html#show-warnings) after executing the  `EXPLAIN` statement. 

- **Time zone support for TIMESTAMP and DATETIME.** As of MySQL 8.0.19, the server accepts a time zone offset with inserted datetime ([`TIMESTAMP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime) and [`DATETIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime)) values. This offset uses the same format as that employed when setting the [`time_zone`](server-administration#sysvar_time_zone) system variable, except that a leading zero is required when the hours portion of the offset is less than 10, and `'-00:00'` is not allowed. Examples of datetime literals that include time zone offsets are `'2019-12-11 10:40:30-05:00'`, `'2003-04-14 03:30:00+10:00'`, and `'2020-01-01 15:35:45+05:30'`.  

 

 

 ​  Time zone offsets are not displayed when selecting datetime  values. 

 ​  Datetime literals incorporating time zone offsets can be  used as prepared statement parameter values. 

 ​  As part of this work, the value used to set the  [`time_zone`](server-administration#sysvar_time_zone) system variable  is now also restricted to the range  `-14:00` to `+14:00`,  inclusive. (It remains possible to assign name values to  `time_zone` such as  `'EST'`,  `'Posix/Australia/Brisbane'`, and  `'Europe/Stockholm'` to this variable,  provided that the MySQL time zone tables are loaded; see  [Populating the Time Zone Tables](server-administration#time-zone-installation)). 

 ​  For more information and examples, see  [Section 5.1.14, “MySQL Server Time Zone Support”](server-administration#time-zone-support), as well as  [Section 11.2.2, “The DATE, DATETIME, and TIMESTAMP Types”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime). 

- **Precise information for JSON schema CHECK constraint failures.** When using [`JSON_SCHEMA_VALID()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-schema-valid) to specify a `CHECK` constraint, MySQL 8.0.19 and later provides precise information about the reasons for failures of such constraints.  

 

 

 ​  For examples and more information, see  [JSON_SCHEMA_VALID() and CHECK constraints](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-validation-functions-constraints). See  also [Section 13.1.20.6, “CHECK Constraints”](sql-statements.html#create-table-check-constraints). 

- **Row and column aliases with ON DUPLICATE KEY UPDATE.** Beginning with MySQL 8.0.19, it is possible to reference the row to be inserted, and, optionally, its columns, using aliases. Consider the following [`INSERT`](sql-statements.html#insert) statement on a table `t` having columns `a` and `b`:  

 

 

 ```
 INSERT INTO t SET a=9,b=5
 ON DUPLICATE KEY UPDATE a=VALUES(a)+VALUES(b);
 ```

 ​  Using the alias `new` for the new row, and,  in some cases, the aliases `m` and  `n` for this row's columns, the  `INSERT` statement can be rewritten in many  different ways, some examples of which are shown here: 

 ```
 INSERT INTO t SET a=9,b=5 AS new
 ON DUPLICATE KEY UPDATE a=new.a+new.b;
 
 INSERT INTO t VALUES(9,5) AS new
 ON DUPLICATE KEY UPDATE a=new.a+new.b;
 
 INSERT INTO t SET a=9,b=5 AS new(m,n)
 ON DUPLICATE KEY UPDATE a=m+n;
 
 INSERT INTO t VALUES(9,5) AS new(m,n)
 ON DUPLICATE KEY UPDATE a=m+n;
 ```

 ​  For more information and examples, see  [Section 13.2.6.2, “INSERT ... ON DUPLICATE KEY UPDATE Statement”](sql-statements.html#insert-on-duplicate). 

- **SQL standard explicit table clause and table value constructor.** Added table value constructors and explicit table clauses according to the SQL standard. These are implemented in MySQL 8.0.19, respectively, as the [`TABLE`](sql-statements.html#table) statement and the [`VALUES`](sql-statements.html#values) statement.  

 

 

 

 

 ​  The [`TABLE`](sql-statements.html#table) statement has the  format `TABLE  *`table_name`*`, and is  equivalent to `SELECT * FROM  *`table_name`*`. It supports  `ORDER BY` and `LIMIT`  clauses ( the latter with optional  `OFFSET`), but does not allow for the  selection of individual table columns.  `TABLE` can be used anywhere that you would  employ the equivalent [`SELECT`](sql-statements.html#select)  statement; this includes joins, unions,  [`INSERT ... SELECT`](sql-statements.html#insert-select), [`REPLACE`](sql-statements.html#replace),  [`CREATE TABLE ... SELECT`](sql-statements.html#create-table-select) statements, and subqueries. For  example:

 - `TABLE t1 UNION TABLE t2` is equivalent to `SELECT * FROM t1 UNION SELECT * FROM t2` 
 - `CREATE TABLE t2 TABLE t1` is equivalent to `CREATE TABLE t2 SELECT * FROM t1` 
 - `SELECT a FROM t1 WHERE b > ANY (TABLE t2)` is equivalent to `SELECT a FROM t1 WHERE b > ANY (SELECT * FROM t2)`.

 ​  [`VALUES`](sql-statements.html#values) can be used to supply  a table value to an [`INSERT`](sql-statements.html#insert),  [`REPLACE`](sql-statements.html#replace), or  [`SELECT`](sql-statements.html#select) statement, and  consists of the `VALUES` keyword followed  by a series of row constructors (`ROW()`)  separated by commas. For example, the statement  `INSERT INTO t1 VALUES ROW(1,2,3), ROW(4,5,6),  ROW(7,8,9)` provides an SQL-compliant equivalent to  the MySQL-specific `INSERT INTO t1 VALUES (1,2,3),  (4,5,6), (7,8,9)`. You can also select from a  [`VALUES`](sql-statements.html#values) table value  constructor just as you would a table, bearing in mind that  you must supply a table alias when doing so, and use this  [`SELECT`](sql-statements.html#select) just as you would any  other; this includes joins, unions, and subqueries. 

 ​  For more information about `TABLE` and  `VALUES`, and for examples of their use,  see the following sections of this documentation:

 - [Section 13.2.12, “TABLE Statement”](sql-statements.html#table) 
 - [Section 13.2.14, “VALUES Statement”](sql-statements.html#values) 
 - [Section 13.1.20.4, “CREATE TABLE ... SELECT Statement”](sql-statements.html#create-table-select) 
 - [Section 13.2.6.1, “INSERT ... SELECT Statement”](sql-statements.html#insert-select) 
 - [Section 13.2.10.2, “JOIN Clause”](sql-statements.html#join) 
 - [Section 13.2.11, “Subqueries”](sql-statements.html#subqueries) 
 - [Section 13.2.10.3, “UNION Clause”](sql-statements.html#union)

- **Optimizer hints for FORCE INDEX, IGNORE INDEX.** MySQL 8.0 introduces index-level optimizer hints which serve as analogs to the traditional index hints as described in [Section 8.9.4, “Index Hints”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#index-hints). The new hints are listed here, along with their `FORCE INDEX` or `IGNORE INDEX` equivalents:

 - [`GROUP_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `FORCE INDEX FOR GROUP BY` 

 ​ [`NO_GROUP_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `IGNORE INDEX FOR GROUP BY` 

 - [`JOIN_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `FORCE INDEX FOR JOIN` 

 ​ [`NO_JOIN_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `IGNORE INDEX FOR JOIN` 

 - [`ORDER_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `FORCE INDEX FOR ORDER BY` 

 ​ [`NO_ORDER_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Equivalent to `IGNORE INDEX FOR ORDER BY` 

 - [`INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Same as [`GROUP_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level) plus [`JOIN_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level) plus [`ORDER_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level); equivalent to `FORCE INDEX` with no modifier 

 ​ [`NO_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level): Same as [`NO_GROUP_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level) plus [`NO_JOIN_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level) plus [`NO_ORDER_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level); equivalent to `IGNORE INDEX` with no modifier

 ​  For example, the following two queries are equivalent: 

 ```
 SELECT a FROM t1 FORCE INDEX (i_a) FOR JOIN WHERE a=1 AND b=2;
 
 SELECT /*+ JOIN_INDEX(t1 i_a) */ a FROM t1 WHERE a=1 AND b=2;
 ```

 ​  The optimizer hints listed previously follow the same basic  rules for syntax and usage as existing index-level optimizer  hints. 

 ​  These optimizer hints are intended to replace `FORCE  INDEX` and `IGNORE INDEX`, which  we plan to deprecate in a future MySQL release, and  subsequently to remove from MySQL. They do not implement a  single exact equivalent for `USE INDEX`;  instead, you can employ one or more of  [`NO_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level),  [`NO_JOIN_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level),  [`NO_GROUP_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level), or  [`NO_ORDER_INDEX`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level) to achieve  the same effect. 

 ​  For further information and examples of use, see  [Index-Level Optimizer Hints](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#optimizer-hints-index-level). 

- **JSON_VALUE() function.** MySQL 8.0.21 implements a new function [`JSON_VALUE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-value) intended to simplify indexing of [`JSON`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json) columns. In its most basic form, it takes as arguments a JSON document and a JSON path pointing to a single value in that document, as well as (optionally) allowing you to specify a return type with the `RETURNING` keyword. `JSON_VALUE(*`json_doc`*, *`path`* RETURNING *`type`*)` is equivalent to this:  

 ```
 CAST(
 JSON_UNQUOTE( JSON_EXTRACT(json_doc, path) )
 AS type
 );
 ```

 ​  You can also specify `ON EMPTY`,  `ON ERROR`, or both clauses, similar to  those employed with  [`JSON_TABLE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-table). 

 ​  You can use `JSON_VALUE()` to create an  index on an expression on a `JSON` column  like this: 

 ```
 CREATE TABLE t1(
 j JSON,
 INDEX i1 ( (JSON_VALUE(j, '$.id' RETURNING UNSIGNED)) )
 );
 
 INSERT INTO t1 VALUES ROW('{"id": "123", "name": "shoes", "price": "49.95"}');
 ```

 ​  A query using this expression, such as that shown here, can  make use of the index: 

 ```
 SELECT name, price FROM t1
 WHERE JSON_VALUE(j, '$.id' RETURNING UNSIGNED) = 123;
 ```

 ​  In many cases, this is simpler than creating a generated  column from the `JSON` column and then  creating an index on the generated column. 

 ​  For more information and examples, see the description of  [`JSON_VALUE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-value). 

- **User comments and user attributes.** MySQL 8.0.21 introduces the ability to set user comments and user attributes when creating or updating user accounts. A user comment consists of arbitrary text passed as the argument to a `COMMENT` clause used with a [`CREATE USER`](sql-statements.html#create-user) or [`ALTER USER`](sql-statements.html#alter-user) statement. A user attribute consists of data in the form of a JSON object passed as the argument to an `ATTRIBUTE` clause used with either of these two statements. The attribute can contain any valid key-value pairs in JSON object notation. Only one of `COMMENT` or `ATTRIBUTE` can be used in a single `CREATE USER` or `ALTER USER` statement.  

 ​  User comments and user attributes are stored together  internally as a JSON object, the comment text as the value  of an element having `comment` as its key.  This information can be retrieved from the  `ATTRIBUTE` column of the  [`INFORMATION_SCHEMA.USER_ATTRIBUTES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-user-attributes-table)  table; since it is in JSON format, you can use MySQL's  JSON function and operators to parse its contents (see  [Section 12.17, “JSON Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-functions)). Successive changes to the  user attribute are merged with its current value as when  using the [`JSON_MERGE_PATCH()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge-patch)  function. 

 ​  Example: 

 ```
 mysql> CREATE USER 'mary'@'localhost' COMMENT 'This is Mary Smith\'s account';
 Query OK, 0 rows affected (0.33 sec)
 
 mysql> ALTER USER 'mary'@'localhost'
 -≫  ATTRIBUTE '{"fname":"Mary", "lname":"Smith"}';
 Query OK, 0 rows affected (0.14 sec)
 
 mysql> ALTER USER 'mary'@'localhost'
 -≫  ATTRIBUTE '{"email":"mary.smith@example.com"}';
 Query OK, 0 rows affected (0.12 sec)
 
 mysql> SELECT
 -> USER,
 -> HOST,
 -> ATTRIBUTE->>"$.fname" AS 'First Name',
 -> ATTRIBUTE->>"$.lname" AS 'Last Name',
 -> ATTRIBUTE->>"$.email" AS 'Email',
 -> ATTRIBUTE->>"$.comment" AS 'Comment'
 -> FROM INFORMATION_SCHEMA.USER_ATTRIBUTES
 -> WHERE USER='mary' AND HOST='localhost'\G
 *************************** 1. row ***************************
 USER: mary
 HOST: localhost
 First Name: Mary
 Last Name: Smith
 Email: mary.smith@example.com
  Comment: This is Mary Smith's account
 1 row in set (0.00 sec)
 ```

 ​  For more information and examples, see  [Section 13.7.1.3, “CREATE USER Statement”](sql-statements.html#create-user), [Section 13.7.1.1, “ALTER USER Statement”](sql-statements.html#alter-user),  and  [Section 25.46, “The INFORMATION_SCHEMA USER_ATTRIBUTES Table”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-user-attributes-table). 

- **New optimizer_switch flags.** MySQL 8.0.21 adds two new flags for the [`optimizer_switch`](server-administration#sysvar_optimizer_switch) system variable, as described in the following list:

 - `prefer_ordering_index` flag 

 ​ By default, MySQL attempts to use an ordered index for any `ORDER BY` or `GROUP BY` query that has a `LIMIT` clause, whenever the optimizer determines that this would result in faster execution. Because it is possible in some cases that choosing a different optimization for such queries actually performs better, it is now possible to disable this optimization by setting the `prefer_ordering_index` flag to `off`. 

 ​ The default value for this flag is `on`. 

 - `subquery_to_derived` flag 

 ​ When this flag is set to `on`, the optimizer transforms eligible scalar subqueries into joins on derived tables. For example, the query `SELECT * FROM t1 WHERE t1.a > (SELECT COUNT(a) FROM t2)` is rewritten as `SELECT t1.a FROM t1 JOIN ( SELECT COUNT(t2.a) AS c FROM t2 ) AS d WHERE t1.a > d.c`. 

 ​ This optimization can be applied to a subquery which is part of a `SELECT`, `WHERE`, `JOIN`, or `HAVING` clause; contains one or more aggregate functions but no `GROUP BY` clause; is not correlated; and does not use any nondeterministic functions. 

 ​ The optimization can also be applied to a table subquery which is the argument to `IN`, `NOT IN`, `EXISTS`, or `NOT EXISTS`, and which does not contain a `GROUP BY`. For example, the query `SELECT * FROM t1 WHERE t1.b < 0 OR t1.a IN (SELECT t2.a + 1 FROM t2)` is rewritten as `SELECT a, b FROM t1 LEFT JOIN (SELECT DISTINCT 1 AS e1, t2.a AS e2 FROM t2) d ON t1.a + 1 = d.e2 WHERE t1.b < 0 OR d.e1 IS NOT NULL`. 

 ​ This optimization is normally disabled, as it does not yield a noticeable performance benefit in most cases, and so the flag is set to `off` by default.

 ​  For more information, see  [Section 8.9.2, “Switchable Optimizations”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#switchable-optimizations). See also  [Section 8.2.1.19, “LIMIT Query Optimization”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#limit-optimization),  [Section 8.2.2.1, “Optimizing IN and EXISTS Subquery Predicates with Semijoin Transformations”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#semijoins), and  [Section 8.2.2.4, “Optimizing Derived Tables, View References, and Common Table Expressions with Merging or Materialization”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#derived-table-optimization). 

- **XML enhancements.** As of MySQL 8.0.21, the [`LOAD XML`](sql-statements.html#load-xml) statement now supports `CDATA` sections in the XML to be imported.  

- **Casting to the YEAR type now supported.** Beginning with MySQL 8.0.22, the server allows casting to [`YEAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#year). Both the [`CAST()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_cast) and [`CONVERT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_convert) functions support single-digit, two-digit, and four-digit `YEAR` values. For one-digit and two-digit values, the allowed range is 0-99. Four-digit values must be in the range 1901-2155. `YEAR` can also be used as the return type for the [`JSON_VALUE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-value) function; this function supports four-digit years only.  

 ​  String, time-and-date, and floating-point values can all be  cast to `YEAR`. Casting of  [`GEOMETRY`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#spatial-type-overview) values to  `YEAR` is not supported. 

 ​  For mroe information, including conversion rules, see the  description of the [`CONVERT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_convert)  function.

### Features Deprecated in MySQL 8.0



​ The following features are deprecated in MySQL 8.0 and may be or will be removed in a future series. Where alternatives are shown, applications should be updated to use them. 

​ For applications that use features deprecated in MySQL 8.0 that have been removed in a higher MySQL series, statements may fail when replicated from a MySQL 8.0 master to a higher-series slave, or may have different effects on master and slave. To avoid such problems, applications that use features deprecated in 8.0 should be revised to avoid them and use alternatives when possible.

-  The `utf8mb3` character set is deprecated.  Please use `utf8mb4` instead. 

 

 

-  Because `caching_sha2_password` is the  default authentication plugin in MySQL 8.0 and provides a  superset of the capabilities of the  `sha256_password` authentication plugin,  `sha256_password` is deprecated and will be  removed in a future MySQL version. MySQL accounts that  authenticate using `sha256_password` should  be migrated to use `caching_sha2_password`  instead. 

 

 

-  The `validate_password` plugin has been  reimplemented to use the server component infrastructure.  The plugin form of `validate_password` is  still available but is deprecated and will be removed in a  future version of MySQL. MySQL installations that use the  plugin should make the transition to using the component  instead. See  [Section 6.4.3.3, “Transitioning to the Password Validation Component”](security#validate-password-transitioning). 

 

 

-  The `ENGINE` clause for the  [`ALTER TABLESPACE`](sql-statements.html#alter-tablespace) and  [`DROP TABLESPACE`](sql-statements.html#drop-tablespace) statements is  deprecated. 

 

 

-  The  [`PAD_CHAR_TO_FULL_LENGTH`](server-administration#sqlmode_pad_char_to_full_length)  SQL mode is deprecated. 

 

 

-  `AUTO_INCREMENT` support is deprecated for  columns of type [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types) and  [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types) (and any synonyms).  Consider removing the `AUTO_INCREMENT`  attribute from such columns, or convert them to an integer  type. 

 

 

-  The `UNSIGNED` attribute is deprecated for  columns of type [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types),  [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types), and  [`DECIMAL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#fixed-point-types) (and any synonyms).  Consider using a simple `CHECK` constraint  instead for such columns. 

 

 

-  `FLOAT(*`M`*,*`D`*)`  and  `DOUBLE(*`M`*,*`D`*)`  syntax to specify the number of digits for columns of type  [`FLOAT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types) and  [`DOUBLE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types) (and any synonyms) is  a nonstandard MySQL extension. This syntax is deprecated. 

 

 

-  The `ZEROFILL` attribute is deprecated for  numeric data types, as is the display width attribute for  integer data types. Consider using an alternative means of  producing the effect of these attributes. For example,  applications could use the  [`LPAD()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_lpad) function to zero-pad  numbers up to the desired width, or they could store the  formatted numbers in [`CHAR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#char)  columns. 

-  For string data types, the `BINARY`  attribute is a nonstandard MySQL extension that is shorthand  for specifying the binary (`_bin`)  collation of the column character set (or of the table  default character set if no column character set is  specified). In MySQL 8.0, this nonstandard use of  `BINARY` is ambiguous because the  `utf8mb4` character set has multiple  `_bin` collations, so the  `BINARY` attribute is deprecated and  support for it will be removed in a future MySQL version.  Applications should be adjusted to use an explicit  `_bin` collation instead. 

 

 

 ​  The use of `BINARY` to specify a data type  or character set remains unchanged. 

-  The nonstandard C-style  [`&&`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and),  [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or), and  [`!`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not) operators  that are synonyms for the standard SQL  [`AND`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and),  [`OR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or), and  [`NOT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not) operators, respectively,  are deprecated. Applications that use the nonstandard  operators should be adjusted to use the standard operators.

 

 

 

 

 

 

 Note

 ​ Use of [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) is deprecated unless the [`PIPES_AS_CONCAT`](server-administration#sqlmode_pipes_as_concat) SQL mode is enabled. In that case, `||` signifies the SQL-standard string concatenation operator).

-  The [`JSON_MERGE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge) function is  deprecated. Use  [`JSON_MERGE_PRESERVE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-merge-preserve)  instead. 

 

 

-  The `SQL_CALC_FOUND_ROWS` query modifier  and accompanying [`FOUND_ROWS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_found-rows)  function are deprecated. See the  [`FOUND_ROWS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_found-rows) description for  information about an alternative strategy. 

 

 

 

 

-  Support for `TABLESPACE =  innodb_file_per_table` and `TABLESPACE =  innodb_temporary` clauses with  [`CREATE TEMPORARY TABLE`](sql-statements.html#create-table) is deprecated as of MySQL 8.0.13. 

 

 

-  For [`SELECT`](sql-statements.html#select) statements, use of  an `INTO` clause after  `FROM` but not at the end of the  [`SELECT`](sql-statements.html#select) is deprecated as of  MySQL 8.0.20. It is preferred to place the  `INTO` at the end of the statement. 

 ​  For [`UNION`](sql-statements.html#union) statements, these  two variants containing `INTO` are  deprecated as of MySQL 8.0.20:

 - In the trailing query block of a query expression, use of `INTO` before `FROM`. 
 - In a parenthesized trailing block of a query expression, use of `INTO`, regardless of its position relative to `FROM`.

 ​  See [Section 13.2.10.1, “SELECT ... INTO Statement”](sql-statements.html#select-into), and  [Section 13.2.10.3, “UNION Clause”](sql-statements.html#union). 

 

 

 

 

-  The [**mysql_upgrade**](programs#mysql-upgrade) client is deprecated  because its capabilities for upgrading the system tables in  the `mysql` system schema and objects in  other schemas have been moved into the MySQL server. See  [Section 2.11.3, “What the MySQL Upgrade Process Upgrades”](installing#upgrading-what-is-upgraded). 

 

 

-  The [`--no-dd-upgrade`](server-administration#option_mysqld_no-dd-upgrade) server  option is deprecated. It is superseded by the  [`--upgrade`](server-administration#option_mysqld_upgrade) option, which  provides finer control over data dictionary and server  upgrade behavior. 

 

 

-  The `mysql_upgrade_info` file, which is  created data directory and used to store the MySQL version  number, is deprecated and will be removed in a future MySQL  version. 

 

 

-  The `relay_log_info_file` system variable  and `--master-info-file` option are  deprecated. Previously, these were used to specify the name  of the relay log info log and master info log when  [`relay_log_info_repository=FILE`](replication#sysvar_relay_log_info_repository)  and  [`master_info_repository=FILE`](replication#sysvar_master_info_repository)  were set, but those settings have been deprecated. The use  of files for the relay log info log and master info log has  been superseded by crash-safe slave tables, which are the  default in MySQL 8.0. 

 

 

 

 

-  The  [`max_length_for_sort_data`](server-administration#sysvar_max_length_for_sort_data)  system variable is now deprecated due to optimizer changes  that make it obsolete and of no effect. 

 

 

-  These legacy parameters for compression of connections to  the server are deprecated: The  [`--compress`](programs#option_general_compress) client  command-line option; the  `MYSQL_OPT_COMPRESS` option for the  [`mysql_options()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-options.html) C API  function; the  [`slave_compressed_protocol`](replication#sysvar_slave_compressed_protocol)  system variable. For information about parameters to use  instead, see  [Section 4.2.8, “Connection Compression Control”](programs#connection-compression-control). 

 

 

 

 

 

 

-  Use of the `MYSQL_PWD` environment variable  to specify a MySQL password is deprecated. 

 

 

-  Use of [`VALUES()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_values) to access new  row values in  [`INSERT ... ON DUPLICATE KEY UPDATE`](sql-statements.html#insert-on-duplicate) is deprecated as of  MySQL 8.0.20. Use aliases for the new row and columns,  instead. 

 

 

 

 

-  Because specifying `ON ERROR` before  `ON EMPTY` when invoking  [`JSON_TABLE()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-table) is counter to  the SQL standard, this syntax is now deprecated in MySQL.  Beginning with MySQL 8.0.20, the server prints a warning  whenever you attempt to do so. When specifying both of these  clauses in a single `JSON_TABLE()`  invocation, make sure that `ON EMPTY` is  used first. 

 

 

-  Columns with index prefixes have never been supported as  part of a table's partitioning key; previously, these  were allowed when creating, altering, or upgrading  partitioned tables but were excluded by the table's  partitioning function, and no warning that this had occurred  was issued by the server. This permissive behavior is now  deprecated, and subject to removal in a future version of  MySQL in which using any such columns in the partitioning  key will cause the [`CREATE TABLE`](sql-statements.html#create-table) or [`ALTER TABLE`](sql-statements.html#alter-table) statement in they occur to be rejected. 

 ​  As of MySQL 8.0.21, whenever columns using index prefixes  are specified as part of the partitioning key, a warning is  generated for each such column. Whenever a  [`CREATE TABLE`](sql-statements.html#create-table) or  [`ALTER TABLE`](sql-statements.html#alter-table) statement is  rejected because all columns in the proposed partitioning  key would have index prefixes, the resulting error now  provides the exact reason for the rejection. In either  instance, this includes cases in which the columns used in  the partitioning function are defined implicitly as those in  the table's primary key by employing an empty  `PARTITION BY KEY()` clause. 

 ​  For more information and examples, see  [Column index prefixes not supported for key partitioning](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/partitioning.html#partitioning-limitations-prefixes). 

 

 

-  The InnoDB memcached plugin is deprecated as of MySQL 8.0.22  and support for it will be removed in a future MySQL  version.

 

 

### Features Removed in MySQL 8.0



​ The following items are obsolete and have been removed in MySQL 8.0. Where alternatives are shown, applications should be updated to use them. 

​ For MySQL 5.7 applications that use features removed in MySQL 8.0, statements may fail when replicated from a MySQL 5.7 master to a MySQL 8.0 slave, or may have different effects on master and slave. To avoid such problems, applications that use features removed in MySQL 8.0 should be revised to avoid them and use alternatives when possible.

-  The `innodb_locks_unsafe_for_binlog` system  variable was removed. The [`READ COMMITTED`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#isolevel_read-committed) isolation level provides similar  functionality. 

 

 

-  The `information_schema_stats` variable,  introduced in MySQL 8.0.0, was removed and replaced by  [`information_schema_stats_expiry`](server-administration#sysvar_information_schema_stats_expiry)  in MySQL 8.0.3. 

 

 

 ​  `information_schema_stats_expiry` defines  an expiration setting for cached  [`INFORMATION_SCHEMA`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html) table  statistics. For more information, see  [Section 8.2.3, “Optimizing INFORMATION_SCHEMA Queries”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#information-schema-optimization). 

-  Code related to obsoleted `InnoDB` system  tables was removed in MySQL 8.0.3.  [`INFORMATION_SCHEMA`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html) views based  on `InnoDB` system tables were replaced by  internal system views on data dictionary tables. Affected  `InnoDB`  [`INFORMATION_SCHEMA`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html) views were  renamed:

 

 **Table 1.1 Renamed InnoDB Information Schema Views**

 | Old Name | New Name |
 | ------------------------- | --------------------- |
 | `INNODB_SYS_COLUMNS` | `INNODB_COLUMNS` |
 | `INNODB_SYS_DATAFILES` | `INNODB_DATAFILES` |
 | `INNODB_SYS_FIELDS` | `INNODB_FIELDS` |
 | `INNODB_SYS_FOREIGN` | `INNODB_FOREIGN` |
 | `INNODB_SYS_FOREIGN_COLS` | `INNODB_FOREIGN_COLS` |
 | `INNODB_SYS_INDEXES` | `INNODB_INDEXES` |
 | `INNODB_SYS_TABLES` | `INNODB_TABLES` |
 | `INNODB_SYS_TABLESPACES` | `INNODB_TABLESPACES` |
 | `INNODB_SYS_TABLESTATS` | `INNODB_TABLESTATS` |
 | `INNODB_SYS_VIRTUAL` | `INNODB_VIRTUAL` |

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 ​  After upgrading to MySQL 8.0.3 or later, update any scripts  that reference previous `InnoDB`  [`INFORMATION_SCHEMA`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html) view names. 

-  The following features related to account management are  removed:

 - Using [`GRANT`](sql-statements.html#grant) to create users. Instead, use [`CREATE USER`](sql-statements.html#create-user). Following this practice makes the `NO_AUTO_CREATE_USER` SQL mode immaterial for [`GRANT`](sql-statements.html#grant) statements, so it too is removed, and an error now is written to the server log when the presence of this value for the `sql_mode` option in the options file prevents [**mysqld**](programs#mysqld) from starting. 

 

 

 - Using [`GRANT`](sql-statements.html#grant) to modify account properties other than privilege assignments. This includes authentication, SSL, and resource-limit properties. Instead, establish such properties at account-creation time with [`CREATE USER`](sql-statements.html#create-user) or modify them afterward with [`ALTER USER`](sql-statements.html#alter-user). 

 - `IDENTIFIED BY PASSWORD '*`auth_string`*'` syntax for [`CREATE USER`](sql-statements.html#create-user) and [`GRANT`](sql-statements.html#grant). Instead, use `IDENTIFIED WITH *`auth_plugin`* AS '*`auth_string`*'` for [`CREATE USER`](sql-statements.html#create-user) and [`ALTER USER`](sql-statements.html#alter-user), where the `'*`auth_string`*'` value is in a format compatible with the named plugin. 

 

 

 ​ Additionally, because `IDENTIFIED BY PASSWORD` syntax was removed, the `log_builtin_as_identified_by_password` system variable is superfluous and was removed. 

 

 

 - The `PASSWORD()` function. Additionally, `PASSWORD()` removal means that [`SET PASSWORD ... = PASSWORD('*`auth_string`*')`](sql-statements.html#set-password) syntax is no longer available. 

 

 

 - The `old_passwords` system variable.

 

 

-  The query cache was removed. Removal includes these items:

 

 

 - The `FLUSH QUERY CACHE` and `RESET QUERY CACHE` statements. 

 

 

 

 

 - These system variables: `query_cache_limit`, `query_cache_min_res_unit`, `query_cache_size`, `query_cache_type`, `query_cache_wlock_invalidate`. 

 

 

 

 

 

 

 

 

 

 

 - These status variables: `Qcache_free_blocks`, `Qcache_free_memory`, `Qcache_hits`, `Qcache_inserts`, `Qcache_lowmem_prunes`, `Qcache_not_cached`, `Qcache_queries_in_cache`, `Qcache_total_blocks`. 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 - These thread states: `checking privileges on cached query`, `checking query cache for query`, `invalidating query cache entries`, `sending cached result to client`, `storing result in query cache`, `Waiting for query cache lock`. 

 

 

 - The `SQL_CACHE` [`SELECT`](sql-statements.html#select) modifier.

 

 

 ​  These deprecated query cache items remain deprecated, but  have no effect, and will be removed in a future MySQL  release:

 - `SQL_NO_CACHE` [`SELECT`](sql-statements.html#select) modifier. 
 - The `ndb_cache_check_time` system variable.

 ​  The `have_query_cache` system variable  remains deprecated, always has a value of  `NO`, and will be removed in a future MySQL  release. 

-  The data dictionary provides information about database  objects, so the server no longer checks directory names in  the data directory to find databases. Consequently, the  `--ignore-db-dir` option and  `ignore_db_dirs` system variables are  extraneous and are removed. 

 

 

 

 

-  The DDL log, also known as the metadata log, has been  removed. Beginning with MySQL 8.0.3, this functionality is  handled by the data dictionary  `innodb_ddl_log` table. See  [Viewing DDL Logs](sql-statements.html#atomic-ddl-view-logs). 

-  The `tx_isolation` and  `tx_read_only` system variables have been  removed. Use `transaction_isolation` and  `transaction_read_only` instead. 

 

 

 

 

-  The `sync_frm` system variable has been  removed because `.frm` files have become  obsolete. 

 

 

-  The `secure_auth` system variable and  `--secure-auth` client option have been  removed. The `MYSQL_SECURE_AUTH` option for  the [`mysql_options()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-options.html) C API  function was removed. 

 

 

 

 

 

 

-  The `multi_range_count` system variable is  removed. 

 

 

-  The `log_warnings` system variable and  `--log-warnings` server option have been  removed. Use the  [`log_error_verbosity`](server-administration#sysvar_log_error_verbosity) system  variable instead. 

 

 

 

 

-  The global scope for the  [`sql_log_bin`](replication#sysvar_sql_log_bin) system variable  was removed. `sql_log_bin` has session  scope only, and applications that rely on accessing  `@@GLOBAL.sql_log_bin` should be adjusted. 

 

 

-  The `metadata_locks_cache_size` and  `metadata_locks_hash_instances` system  variables are removed. 

 

 

 

 

-  The unused `date_format`,  `datetime_format`,  `time_format`, and  `max_tmp_tables` system variables are  removed. 

 

 

 

 

 

 

 

 

-  These deprecated compatibility SQL modes are removed:  `DB2`, `MAXDB`,  `MSSQL`, `MYSQL323`,  `MYSQL40`, `ORACLE`,  `POSTGRESQL`,  `NO_FIELD_OPTIONS`,  `NO_KEY_OPTIONS`,  `NO_TABLE_OPTIONS`. They can no longer be  assigned to the `sql_mode` system variable  or used as permitted values for the  [**mysqldump**](programs#mysqldump)  [`--compatible`](programs#option_mysqldump_compatible) option. 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 ​  Removal of `MAXDB` means that the  [`TIMESTAMP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime) data type for  [`CREATE TABLE`](sql-statements.html#create-table) or  [`ALTER TABLE`](sql-statements.html#alter-table) is treated as  [`TIMESTAMP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime), and is no longer  treated as [`DATETIME`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#datetime). 

-  The deprecated `ASC` or  `DESC` qualifiers for `GROUP  BY` clauses are removed. Queries that previously  relied on `GROUP BY` sorting may produce  results that differ from previous MySQL versions. To produce  a given sort order, provide an `ORDER BY`  clause. 

 

 

-  The `EXTENDED` and  `PARTITIONS` keywords for the  [`EXPLAIN`](sql-statements.html#explain) statement have been  removed. These keywords are unnecessary because their effect  is always enabled. 

 

 

 

 

-  These encryption-related items are removed:

 - The `ENCODE()` and `DECODE()` functions. 

 

 

 

 

 - The `ENCRYPT()` function. 

 

 

 - The `DES_ENCRYPT()`, and `DES_DECRYPT()` functions, the `--des-key-file` option, the `have_crypt` system variable, the `DES_KEY_FILE` option for the [`FLUSH`](sql-statements.html#flush) statement, and the `HAVE_CRYPT` **CMake** option.

 

 

 

 

 

 

 

 

 

 

 

 

 ​  In place of the removed encryption functions: For  `ENCRYPT()`, consider using  [`SHA2()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_sha2) instead for one-way  hashing. For the others, consider using  [`AES_ENCRYPT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_aes-encrypt) and  [`AES_DECRYPT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_aes-decrypt) instead. 

-  In MySQL 5.7, several spatial functions  available under multiple names were deprecated to move in  the direction of making the spatial function namespace more  consistent, the goal being that each spatial function name  begin with `ST_` if it performs an exact  operation, or with `MBR` if it performs an  operation based on minimum bounding rectangles. In MySQL  8.0, the deprecated functions are removed to  leave only the corresponding `ST_` and  `MBR` functions:

 - These functions are removed in favor of the `MBR` names: `Contains()`, `Disjoint()`, `Equals()`, `Intersects()`, `Overlaps()`, `Within()`. 

 

 

 

 

 

 

 

 

 

 

 

 

 - These functions are removed in favor of the `ST_` names: `Area()`, `AsBinary()`, `AsText()`, `AsWKB()`, `AsWKT()`, `Buffer()`, `Centroid()`, `ConvexHull()`, `Crosses()`, `Dimension()`, `Distance()`, `EndPoint()`, `Envelope()`, `ExteriorRing()`, `GeomCollFromText()`, `GeomCollFromWKB()`, `GeomFromText()`, `GeomFromWKB()`, `GeometryCollectionFromText()`, `GeometryCollectionFromWKB()`, `GeometryFromText()`, `GeometryFromWKB()`, `GeometryN()`, `GeometryType()`, `InteriorRingN()`, `IsClosed()`, `IsEmpty()`, `IsSimple()`, `LineFromText()`, `LineFromWKB()`, `LineStringFromText()`, `LineStringFromWKB()`, `MLineFromText()`, `MLineFromWKB()`, `MPointFromText()`, `MPointFromWKB()`, `MPolyFromText()`, `MPolyFromWKB()`, `MultiLineStringFromText()`, `MultiLineStringFromWKB()`, `MultiPointFromText()`, `MultiPointFromWKB()`, `MultiPolygonFromText()`, `MultiPolygonFromWKB()`, `NumGeometries()`, `NumInteriorRings()`, `NumPoints()`, `PointFromText()`, `PointFromWKB()`, `PointN()`, `PolyFromText()`, `PolyFromWKB()`, `PolygonFromText()`, `PolygonFromWKB()`, `SRID()`, `StartPoint()`, `Touches()`, `X()`, `Y()`. 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 - `GLength()` is removed in favor of [`ST_Length()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_st-length).

 

 

-  The functions described in  [Section 12.16.4, “Functions That Create Geometry Values from WKB Values”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#gis-wkb-functions) previously accepted  either WKB strings or geometry arguments. Geometry arguments  are no longer permitted and produce an error. See that  section for guidelines for migrating queries away from using  geometry arguments. 

 

 

-  The parser no longer treats `\N` as a  synonym for `NULL` in SQL statements. Use  `NULL` instead. 

 

 

 ​  This change does not affect text file import or export  operations performed with [`LOAD DATA`](sql-statements.html#load-data) or  [`SELECT ... INTO OUTFILE`](sql-statements.html#select-into), for which `NULL`  continues to be represented by `\N`. See  [Section 13.2.7, “LOAD DATA Statement”](sql-statements.html#load-data). 

-  `PROCEDURE ANALYSE()` syntax is removed. 

 

 

-  The client-side `--ssl` and  `--ssl-verify-server-cert` options have been  removed. Use  [`--ssl-mode=REQUIRED`](programs#option_general_ssl-mode) instead  of `--ssl=1` or  `--enable-ssl`. Use  [`--ssl-mode=DISABLED`](programs#option_general_ssl-mode) instead  of `--ssl=0`, `--skip-ssl`, or  `--disable-ssl`. Use  [`--ssl-mode=VERIFY_IDENTITY`](programs#option_general_ssl-mode)  instead of `--ssl-verify-server-cert`  options. (The server-side  [`--ssl`](server-administration#option_mysqld_ssl) option remains  unchanged.) 

 

 

 

 

 ​  For the C API, `MYSQL_OPT_SSL_ENFORCE` and  `MYSQL_OPT_SSL_VERIFY_SERVER_CERT` options  for [`mysql_options()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-options.html)  correspond to the client-side `--ssl` and  `--ssl-verify-server-cert` options and are  removed. Use `MYSQL_OPT_SSL_MODE` with an  option value of `SSL_MODE_REQUIRED` or  `SSL_MODE_VERIFY_IDENTITY` instead. 

 

 

 

 

-  The `--temp-pool` server option was removed. 

 

 

-  The `ignore_builtin_innodb` system variable  is removed. 

 

 

-  The server no longer performs conversion of pre-MySQL 5.1  database names containing special characters to 5.1 format  with the addition of a `#mysql50#` prefix.  Because these conversions are no longer performed, the  `--fix-db-names` and  `--fix-table-names` options for  [**mysqlcheck**](programs#mysqlcheck), the `UPGRADE DATA  DIRECTORY NAME` clause for the  [`ALTER DATABASE`](sql-statements.html#alter-database) statement, and  the `Com_alter_db_upgrade` status variable  are removed. 

 

 

 

 

 

 

 

 

 

 

 ​  Upgrades are supported only from one major version to  another (for example, 5.0 to 5.1, or 5.1 to 5.5), so there  should be little remaining need for conversion of older 5.0  database names to current versions of MySQL. As a  workaround, upgrade a MySQL 5.0 installation to MySQL 5.1  before upgrading to a more recent release. 

-  The **mysql_install_db** program has been  removed from MySQL distributions. Data directory  initialization should be performed by invoking  [**mysqld**](programs#mysqld) with the  [`--initialize`](server-administration#option_mysqld_initialize) or  [`--initialize-insecure`](server-administration#option_mysqld_initialize-insecure) option  instead. In addition, the `--bootstrap`  option for [**mysqld**](programs#mysqld) that was used by  **mysql_install_db** was removed, and the  `INSTALL_SCRIPTDIR` `CMake`  option that controlled the installation location for  **mysql_install_db** was removed. 

 

 

 

 

 

 

-  The generic partitioning handler was removed from the MySQL  server. In order to support partitioning of a given table,  the storage engine used for the table must now provide its  own (“native”) partitioning handler. The  `--partition` and  `--skip-partition` options are removed from  the MySQL Server, and partitioning-related entries are no  longer shown in the output of [`SHOW PLUGINS`](sql-statements.html#show-plugins) or in the  [`INFORMATION_SCHEMA.PLUGINS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-plugins-table)  table. 

 

 

 

 

 ​  Two MySQL storage engines currently provide native  partitioning support: [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html)  and [`NDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html). Of these, only  `InnoDB` is supported in MySQL  8.0. Any attempt to create partitioned tables  in MySQL 8.0 using any other storage engine  fails. 

 **Ramifications for upgrades.** The direct upgrade of a partitioned table using a storage engine other than `InnoDB` (such as [`MyISAM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/storage-engines.html#myisam-storage-engine)) from MySQL 5.7 (or earlier) to MySQL 8.0 is not supported. There are two options for handling such a table:

 - Remove the table's partitioning, using [`ALTER TABLE ... REMOVE PARTITIONING`](sql-statements.html#alter-table-partition-operations). 
 - Change the storage engine used for the table to `InnoDB`, with [`ALTER TABLE ... ENGINE=INNODB`](sql-statements.html#alter-table).

 ​  At least one of the two operations just listed must be  performed for each partitioned non-`InnoDB`  table prior to upgrading the server to MySQL  8.0. Otherwise, such a table cannot be used  following the upgrade. 

 ​  Due to the fact that table creation statements that would  result in a partitioned table using a storage engine without  partitioning support now fail with an error  (ER_CHECK_NOT_IMPLEMENTED), you must  make sure that any statements in a dump file (such as that  written by [**mysqldump**](programs#mysqldump)) from an older  version of MySQL that you wish to import into a MySQL  8.0 server that create partitioned tables do  not also specify a storage engine such as  `MyISAM` that has no native partitioning  handler. You can do this by performing either of the  following:

 - Remove any references to partitioning from `CREATE TABLE` statements that use a value for the `STORAGE ENGINE` option other than `InnoDB`. 
 - Specifying the storage engine as `InnoDB`, or allow `InnoDB` to be used as the table's storage engine by default.

 ​  For more information, see  [Section 23.6.2, “Partitioning Limitations Relating to Storage Engines”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/partitioning.html#partitioning-limitations-storage-engines). 

-  System and status variable information is no longer  maintained in the `INFORMATION_SCHEMA`.  These tables are removed:  `GLOBAL_VARIABLES`,  `SESSION_VARIABLES`,  `GLOBAL_STATUS`,  `SESSION_STATUS`. Use the corresponding  Performance Schema tables instead. See  [Section 26.12.14, “Performance Schema System Variable Tables”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-system-variable-tables),  and  [Section 26.12.15, “Performance Schema Status Variable Tables”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-status-variable-tables).  In addition, the `show_compatibility_56`  system variable was removed. It was used in the transition  period during which system and status variable information  in `INFORMATION_SCHEMA` tables was moved to  Performance Schema tables, and is no longer needed. These  status variables are removed:  `Slave_heartbeat_period`,  `Slave_last_heartbeat`,  `Slave_received_heartbeats`,  `Slave_retried_transactions`,  `Slave_running`. The information they  provided is available in Performance Schema tables; see  [Migrating to Performance Schema System and Status Variable Tables](https://dev.mysql.com/doc/refman/5.7/en/performance-schema-variable-table-migration.html). 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

-  The Performance Schema `setup_timers` table  was removed, as was the `TICK` row in the  [`performance_timers`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-performance-timers-table) table. 

 

 

 

 

-  The `libmysqld` embedded server library is  removed, along with:

 

 

 

 

 - The [`mysql_options()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-options.html) `MYSQL_OPT_GUESS_CONNECTION`, `MYSQL_OPT_USE_EMBEDDED_CONNECTION`, `MYSQL_OPT_USE_REMOTE_CONNECTION`, and `MYSQL_SET_CLIENT_IP` options 
 - The [**mysql_config**](programs#mysql-config) `--libmysqld-libs`, `--embedded-libs`, and `--embedded` options 
 - The **CMake** `WITH_EMBEDDED_SERVER`, `WITH_EMBEDDED_SHARED_LIBRARY`, and `INSTALL_SECURE_FILE_PRIV_EMBEDDEDDIR` options 
 - The (undocumented) [**mysql**](programs#mysql) `--server-arg` option 
 - The **mysqltest** `--embedded-server`, `--server-arg`, and `--server-file` options 
 - The **mysqltest_embedded** and **mysql_client_test_embedded** test programs

-  The **mysql_plugin** utility was removed.  Alternatives include loading plugins at server startup using  the [`--plugin-load`](server-administration#option_mysqld_plugin-load) or  [`--plugin-load-add`](server-administration#option_mysqld_plugin-load-add) option, or  at runtime using the [`INSTALL PLUGIN`](sql-statements.html#install-plugin) statement. 

 

 

-  The **resolveip** utility is removed.  **nslookup**, **host**, or  **dig** can be used instead. 

 

 

-  The **resolve_stack_dump** utility is  removed. Stack traces from official MySQL builds are always  symbolized, so there is no need to use  **resolve_stack_dump**. 

 

 

-  The following server error codes are not used and have been  removed. Applications that test specifically for any of  these errors should be updated. 

 

 

 ```
 ER_BINLOG_READ_EVENT_CHECKSUM_FAILURE
 ER_BINLOG_ROW_RBR_TO_SBR
 ER_BINLOG_ROW_WRONG_TABLE_DEF
 ER_CANT_ACTIVATE_LOG
 ER_CANT_CHANGE_GTID_NEXT_IN_TRANSACTION
 ER_CANT_CREATE_FEDERATED_TABLE
 ER_CANT_CREATE_SROUTINE
 ER_CANT_DELETE_FILE
 ER_CANT_GET_WD
 ER_CANT_SET_GTID_PURGED_WHEN_GTID_MODE_IS_OFF
 ER_CANT_SET_WD
 ER_CANT_WRITE_LOCK_LOG_TABLE
 ER_CREATE_DB_WITH_READ_LOCK
 ER_CYCLIC_REFERENCE
 ER_DB_DROP_DELETE
 ER_DELAYED_NOT_SUPPORTED
 ER_DIFF_GROUPS_PROC
 ER_DISK_FULL
 ER_DROP_DB_WITH_READ_LOCK
 ER_DROP_USER
 ER_DUMP_NOT_IMPLEMENTED
 ER_ERROR_DURING_CHECKPOINT
 ER_ERROR_ON_CLOSE
 ER_EVENTS_DB_ERROR
 ER_EVENT_CANNOT_DELETE
 ER_EVENT_CANT_ALTER
 ER_EVENT_COMPILE_ERROR
 ER_EVENT_DATA_TOO_LONG
 ER_EVENT_DROP_FAILED
 ER_EVENT_MODIFY_QUEUE_ERROR
 ER_EVENT_NEITHER_M_EXPR_NOR_M_AT
 ER_EVENT_OPEN_TABLE_FAILED
 ER_EVENT_STORE_FAILED
 ER_EXEC_STMT_WITH_OPEN_CURSOR
 ER_FAILED_ROUTINE_BREAK_BINLOG
 ER_FLUSH_MASTER_BINLOG_CLOSED
 ER_FORM_NOT_FOUND
 ER_FOUND_GTID_EVENT_WHEN_GTID_MODE_IS_OFF__UNUSED
 ER_FRM_UNKNOWN_TYPE
 ER_GOT_SIGNAL
 ER_GRANT_PLUGIN_USER_EXISTS
 ER_GTID_MODE_REQUIRES_BINLOG
 ER_GTID_NEXT_IS_NOT_IN_GTID_NEXT_LIST
 ER_HASHCHK
 ER_INDEX_REBUILD
 ER_INNODB_NO_FT_USES_PARSER
 ER_LIST_OF_FIELDS_ONLY_IN_HASH_ERROR
 ER_LOAD_DATA_INVALID_COLUMN_UNUSED
 ER_LOGGING_PROHIBIT_CHANGING_OF
 ER_MALFORMED_DEFINER
 ER_MASTER_KEY_ROTATION_ERROR_BY_SE
 ER_NDB_CANT_SWITCH_BINLOG_FORMAT
 ER_NEVER_USED
 ER_NISAMCHK
 ER_NO_CONST_EXPR_IN_RANGE_OR_LIST_ERROR
 ER_NO_FILE_MAPPING
 ER_NO_GROUP_FOR_PROC
 ER_NO_RAID_COMPILED
 ER_NO_SUCH_KEY_VALUE
 ER_NO_SUCH_PARTITION__UNUSED
 ER_OBSOLETE_CANNOT_LOAD_FROM_TABLE
 ER_OBSOLETE_COL_COUNT_DOESNT_MATCH_CORRUPTED
 ER_ORDER_WITH_PROC
 ER_PARTITION_SUBPARTITION_ERROR
 ER_PARTITION_SUBPART_MIX_ERROR
 ER_PART_STATE_ERROR
 ER_PASSWD_LENGTH
 ER_QUERY_ON_MASTER
 ER_RBR_NOT_AVAILABLE
 ER_SKIPPING_LOGGED_TRANSACTION
 ER_SLAVE_CHANNEL_DELETE
 ER_SLAVE_MULTIPLE_CHANNELS_HOST_PORT
 ER_SLAVE_MUST_STOP
 ER_SLAVE_WAS_NOT_RUNNING
 ER_SLAVE_WAS_RUNNING
 ER_SP_GOTO_IN_HNDLR
 ER_SP_PROC_TABLE_CORRUPT
 ER_SQL_MODE_NO_EFFECT
 ER_SR_INVALID_CREATION_CTX
 ER_TABLE_NEEDS_UPG_PART
 ER_TOO_MUCH_AUTO_TIMESTAMP_COLS
 ER_UNEXPECTED_EOF
 ER_UNION_TABLES_IN_DIFFERENT_DIR
 ER_UNSUPPORTED_BY_REPLICATION_THREAD
 ER_UNUSED1
 ER_UNUSED2
 ER_UNUSED3
 ER_UNUSED4
 ER_UNUSED5
 ER_UNUSED6
 ER_VIEW_SELECT_DERIVED_UNUSED
 ER_WRONG_MAGIC
 ER_WSAS_FAILED
 ```

-  The deprecated `INFORMATION_SCHEMA`  [`INNODB_LOCKS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-locks-table) and  [`INNODB_LOCK_WAITS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-lock-waits-table) tables are  removed. Use the Performance Schema  [`data_locks`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-data-locks-table) and  [`data_lock_waits`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-data-lock-waits-table) tables instead.

 

 

 

 

 Note

 ​ In MySQL 5.7, the `LOCK_TABLE` column in the [`INNODB_LOCKS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-locks-table) table and the `locked_table` column in the `sys` schema [`innodb_lock_waits`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/sys-schema.html#sys-innodb-lock-waits) and [`x$innodb_lock_waits`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/sys-schema.html#sys-innodb-lock-waits) views contain combined schema/table name values. In MySQL 8.0, the [`data_locks`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/performance-schema.html#performance-schema-data-locks-table) table and the `sys` schema views contain separate schema name and table name columns. See [Section 27.4.3.9, “The innodb_lock_waits and x$innodb_lock_waits Views”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/sys-schema.html#sys-innodb-lock-waits).

-  `InnoDB` no longer supports compressed  temporary tables. When  [`innodb_strict_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_strict_mode) is  enabled (the default),  [`CREATE TEMPORARY TABLE`](sql-statements.html#create-table) returns an error if  `ROW_FORMAT=COMPRESSED` or  `KEY_BLOCK_SIZE` is specified. If  [`innodb_strict_mode`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_strict_mode) is  disabled, warnings are issued and the temporary table is  created using a non-compressed row format. 

 

 

-  `InnoDB` no longer creates  `.isl` files (`InnoDB`  Symbolic Link files) when creating tablespace data files  outside of the MySQL data directory. The  [`innodb_directories`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_directories) option  now supports locating tablespace files created outside of  the data directory. 

 ​  With this change, moving a remote tablespace while the  server is offline by manually modifying an  `.isl` file is no longer supported.  Moving remote tablespace files is now supported by the  [`innodb_directories`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_directories) option.  See [Section 15.6.3.6, “Moving Tablespace Files While the Server is Offline”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-moving-data-files-offline). 

 

 

-  The following `InnoDB` file format  variables were removed:

 - `innodb_file_format` 

 

 

 - `innodb_file_format_check` 

 

 

 - `innodb_file_format_max` 

 

 

 - `innodb_large_prefix`

 

 

 ​  File format variables were necessary for creating tables  compatible with earlier versions of  `InnoDB` in MySQL 5.1. Now that MySQL 5.1  has reached the end of its product lifecycle, these options  are no longer required. 

 ​  The `FILE_FORMAT` column was removed from  the [`INNODB_TABLES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-tables-table) and  [`INNODB_TABLESPACES`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-tablespaces-table) Information  Schema tables. 

 

 

-  The `innodb_support_xa` system variable,  which enables support for two-phase commit in XA  transactions, was removed. `InnoDB` support  for two-phase commit in XA transactions is always enabled. 

 

 

-  Support for DTrace was removed. 

 

 

-  The `JSON_APPEND()` function was removed.  Use [`JSON_ARRAY_APPEND()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_json-array-append)  instead. 

 

 

-  Support for placing table partitions in shared  `InnoDB` tablespaces was removed in MySQL  8.0.13. Shared tablespaces include the  `InnoDB` system tablespace and general  tablespaces. For information about identifying partitions in  shared tablespaces and moving them to file-per-table  tablespaces, see [Section 2.11.5, “Preparing Your Installation for Upgrade”](installing#upgrade-prerequisites). 

 

 

-  Support for setting user variables in statements other than  [`SET`](sql-statements.html#set-variable)  was deprecated in MySQL 8.0.13. This functionality is  subject to removal in MySQL 9.0. 

 

 

-  The `--ndb` [**perror**](programs#perror) option  was removed. Use the [**ndb_perror**](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html#mysql-cluster-programs-ndb-perror) utility  instead. 

 

 

-  The `innodb_undo_logs` variable was  removed. The  [`innodb_rollback_segments`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_rollback_segments)  variables performs the same function and should be used  instead. 

 

 

-  The `Innodb_available_undo_logs` status  variable was removed. The number of available rollback  segments per tablespace may be retrieved using `SHOW  VARIABLES LIKE 'innodb_rollback_segments';` 

 

 

-  As of MySQL 8.0.14, the previously deprecated  [`innodb_undo_tablespaces`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_undo_tablespaces)  variable is no longer configurable. For more information,  see [Section 15.6.3.4, “Undo Tablespaces”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#innodb-undo-tablespaces). 

 

 

-  Support for the `ALTER TABLE ... UPGRADE  PARTITIONING` statement has been removed. 

 

 

-  As of MySQL 8.0.16, support for the  [`internal_tmp_disk_storage_engine`](server-administration#sysvar_internal_tmp_disk_storage_engine)  system variable has been removed; internal temporary tables  on disk now always use the  [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) storage engine. See  [Storage Engine for On-Disk Internal Temporary Tables](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/optimization.html#internal-temporary-tables-engines-disk),for  more information. 

 

 

-  The [`DISABLE_SHARED`](installing#option_cmake_disable_shared)  **CMake** option was unused and has been  removed.

 

 

## 1.5 Server and Status Variables and Options Added, Deprecated, or Removed in MySQL 8.0

​ This section lists server variables, status variables, and options that were added for the first time, have been deprecated, or have been removed in MySQL 8.0.

- [Options and Variables Introduced in MySQL 8.0](#optvars-added) 
- [Options and Variables Deprecated in MySQL 8.0](#optvars-deprecated) 
- [Options and Variables Removed in MySQL 8.0](#optvars-removed)

### Options and Variables Introduced in MySQL 8.0

​ The following system variables, status variables, and options are new in MySQL 8.0, and have not been included in any previous release series.



- `Acl_cache_items_count`: Number of cached privilege objects. Added in MySQL 8.0.0. 
- `Audit_log_current_size`: Audit log file current size. Added in MySQL 8.0.11. 
- `Audit_log_event_max_drop_size`: Size of largest dropped audited event. Added in MySQL 8.0.11. 
- `Audit_log_events`: Number of handled audited events. Added in MySQL 8.0.11. 
- `Audit_log_events_filtered`: Number of filtered audited events. Added in MySQL 8.0.11. 
- `Audit_log_events_lost`: Number of dropped audited events. Added in MySQL 8.0.11. 
- `Audit_log_events_written`: Number of written audited events. Added in MySQL 8.0.11. 
- `Audit_log_total_size`: Combined size of written audited events. Added in MySQL 8.0.11. 
- `Audit_log_write_waits`: Number of write-delayed audited events. Added in MySQL 8.0.11. 
- `Authentication_ldap_sasl_supported_methods`: Supported authentication methods for SASL LDAP authentication. Added in MySQL 8.0.21. 
- `Caching_sha2_password_rsa_public_key`: caching_sha2_password authentication plugin RSA public key value. Added in MySQL 8.0.4. 
- `Com_alter_resource_group`: Count of ALTER RESOURCE GROUP statements. Added in MySQL 8.0.3. 
- `Com_alter_user_default_role`: Count of ALTER USER ... DEFAULT ROLE statements. Added in MySQL 8.0.0. 
- `Com_clone`: Count of CLONE statements. Added in MySQL 8.0.2. 
- `Com_create_resource_group`: Count of CREATE RESOURCE GROUP statements. Added in MySQL 8.0.3. 
- `Com_create_role`: Count of CREATE ROLE statements. Added in MySQL 8.0.0. 
- `Com_drop_resource_group`: Count of DROP RESOURCE GROUP statements. Added in MySQL 8.0.3. 
- `Com_drop_role`: Count of DROP ROLE statements. Added in MySQL 8.0.0. 
- `Com_grant_roles`: Count of GRANT ROLE statements. Added in MySQL 8.0.0. 
- `Com_install_component`: Count of INSTALL COMPONENT statements. Added in MySQL 8.0.0. 
- `Com_restart`: Count of RESTART statements. Added in MySQL 8.0.4. 
- `Com_revoke_roles`: Count of REVOKE ROLES statements. Added in MySQL 8.0.0. 
- `Com_set_resource_group`: Count of SET RESOURCE GROUP statements. Added in MySQL 8.0.3. 
- `Com_set_role`: Count of SET ROLE statements. Added in MySQL 8.0.0. 
- `Com_uninstall_component`: Count of UINSTALL COMPONENT statements. Added in MySQL 8.0.0. 
- `Compression_algorithm`: Compression algorithm for current connection. Added in MySQL 8.0.18. 
- `Compression_level`: Compression level for current connection. Added in MySQL 8.0.18. 
- `Connection_control_delay_generated`: How many times the server delayed a connection request. Added in MySQL 8.0.1. 
- `Current_tls_ca`: Current value of ssl_ca system variable. Added in MySQL 8.0.16. 
- `Current_tls_capath`: Current value of ssl_capath system variable. Added in MySQL 8.0.16. 
- `Current_tls_cert`: Current value of ssl_cert system variable. Added in MySQL 8.0.16. 
- `Current_tls_cipher`: Current value of ssl_cipher system variable. Added in MySQL 8.0.16. 
- `Current_tls_ciphersuites`: Current value of tsl_ciphersuites system variable. Added in MySQL 8.0.16. 
- `Current_tls_crl`: Current value of ssl_crl system variable. Added in MySQL 8.0.16. 
- `Current_tls_crlpath`: Current value of ssl_crlpath system variable. Added in MySQL 8.0.16. 
- `Current_tls_key`: Current value of ssl_key system variable. Added in MySQL 8.0.16. 
- `Current_tls_version`: Current value of tls_version system variable. Added in MySQL 8.0.16. 
- `Firewall_access_denied`: Number of statements rejected by MySQL Enterprise Firewall. Added in MySQL 8.0.11. 
- `Firewall_access_granted`: Number of statements accepted by MySQL Enterprise Firewall. Added in MySQL 8.0.11. 
- `Firewall_cached_entries`: Number of statements recorded by MySQL Enterprise Firewall. Added in MySQL 8.0.11. 
- `Innodb_redo_log_enabled`: InnoDB redo log status. Added in MySQL 8.0.21. 
- `Innodb_system_rows_deleted`: Number of rows deleted from system schema tables. Added in MySQL 8.0.19. 
- `Innodb_system_rows_inserted`: Number of rows inserted into system schema tables. Added in MySQL 8.0.19. 
- `Innodb_system_rows_read`: Number of rows read from system schema tables. Added in MySQL 8.0.19. 
- `Innodb_undo_tablespaces_active`: The number of active undo tablespaces. Added in MySQL 8.0.14. 
- `Innodb_undo_tablespaces_explicit`: The number of user-created undo tablespaces. Added in MySQL 8.0.14. 
- `Innodb_undo_tablespaces_implicit`: The number of undo tablespaces created by InnoDB. Added in MySQL 8.0.14. 
- `Innodb_undo_tablespaces_total`: The total number of undo tablespaces. Added in MySQL 8.0.14. 
- `Mysqlx_bytes_received_compressed_payload`: Number of bytes received as compressed message payloads, measured before decompression. Added in MySQL 8.0.19. 
- `Mysqlx_bytes_received_uncompressed_frame`: Number of bytes received as compressed message payloads, measured after decompression. Added in MySQL 8.0.19. 
- `Mysqlx_bytes_sent_compressed_payload`: Number of bytes sent as compressed message payloads, measured after compression. Added in MySQL 8.0.19. 
- `Mysqlx_bytes_sent_uncompressed_frame`: Number of bytes sent as compressed message payloads, measured before compression. Added in MySQL 8.0.19. 
- `Mysqlx_compression_algorithm`: The compression algorithm in use for the X Protocol connection for this session. Added in MySQL 8.0.20. 
- `Mysqlx_compression_level`: The compression level in use for the X Protocol connection for this session. Added in MySQL 8.0.20. 
- `Secondary_engine_execution_count`: For future use. Added in MySQL 8.0.13. 
- `activate_all_roles_on_login`: Whether to activate all user roles at connect time. Added in MySQL 8.0.2. 
- `admin-ssl`: Enable connection encryption. Added in MySQL 8.0.21. 
- `admin_address`: IP address to bind to for connections on administrative interface. Added in MySQL 8.0.14. 
- `admin_port`: TCP/IP number to use for connections on administrative interface. Added in MySQL 8.0.14. 
- `admin_ssl_ca`: File that contains list of trusted SSL Certificate Authorities. Added in MySQL 8.0.21. 
- `admin_ssl_capath`: Directory that contains trusted SSL Certificate Authority certificate files. Added in MySQL 8.0.21. 
- `admin_ssl_cert`: File that contains X.509 certificate. Added in MySQL 8.0.21. 
- `admin_ssl_cipher`: Permissible ciphers for connection encryption. Added in MySQL 8.0.21. 
- `admin_ssl_crl`: File that contains certificate revocation lists. Added in MySQL 8.0.21. 
- `admin_ssl_crlpath`: Directory that contains certificate revocation list files. Added in MySQL 8.0.21. 
- `admin_ssl_key`: File that contains X.509 key. Added in MySQL 8.0.21. 
- `admin_tls_ciphersuites`: Permissible TLSv1.3 ciphersuites for encrypted connections. Added in MySQL 8.0.21. 
- `admin_tls_version`: Permissible TLS protocols for encrypted connections. Added in MySQL 8.0.21. 
- `audit-log`: Whether to activate the audit log plugin. Added in MySQL 8.0.11. 
- `audit_log_buffer_size`: The size of the audit log buffer. Added in MySQL 8.0.11. 
- `audit_log_compression`: Audit log file compression method. Added in MySQL 8.0.11. 
- `audit_log_connection_policy`: Audit logging policy for connection-related events. Added in MySQL 8.0.11. 
- `audit_log_current_session`: Whether to audit current session. Added in MySQL 8.0.11. 
- `audit_log_encryption`: Audit log file encryption method. Added in MySQL 8.0.11. 
- `audit_log_exclude_accounts`: Accounts not to audit. Added in MySQL 8.0.11. 
- `audit_log_file`: The name of the audit log file. Added in MySQL 8.0.11. 
- `audit_log_filter_id`: ID of current audit log filter. Added in MySQL 8.0.11. 
- `audit_log_flush`: Close and reopen the audit log file. Added in MySQL 8.0.11. 
- `audit_log_format`: The audit log file format. Added in MySQL 8.0.11. 
- `audit_log_include_accounts`: Accounts to audit. Added in MySQL 8.0.11. 
- `audit_log_password_history_keep_days`: Number of days to keep archived audit log encryption passwords. Added in MySQL 8.0.17. 
- `audit_log_policy`: Audit logging policy. Added in MySQL 8.0.11. 
- `audit_log_read_buffer_size`: Audit log file read buffer size. Added in MySQL 8.0.11. 
- `audit_log_rotate_on_size`: Close and reopen the audit log file at a certain size. Added in MySQL 8.0.11. 
- `audit_log_statement_policy`: Audit logging policy for statement-related events. Added in MySQL 8.0.11. 
- `audit_log_strategy`: The audit logging strategy. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_auth_method_name`: Authentication method name. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_bind_base_dn`: LDAP server base distinguished name. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_bind_root_dn`: LDAP server root distinguished name. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_bind_root_pwd`: LDAP server root bind password. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_ca_path`: LDAP server certificate authority file name. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_group_search_attr`: LDAP server group search attribute. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_group_search_filter`: LDAP custom group search filter. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_init_pool_size`: LDAP server initial connection pool size. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_log_status`: LDAP server log level. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_max_pool_size`: LDAP server maximum connection pool size. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_referral`: Whether to enable LDAP search referral. Added in MySQL 8.0.20. 
- `authentication_ldap_sasl_server_host`: LDAP server host name or IP address. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_server_port`: LDAP server port number. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_tls`: Whether to use encrypted connections to LDAP server. Added in MySQL 8.0.11. 
- `authentication_ldap_sasl_user_search_attr`: LDAP server user search attribute. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_auth_method_name`: Authentication method name. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_bind_base_dn`: LDAP server base distinguished name. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_bind_root_dn`: LDAP server root distinguished name. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_bind_root_pwd`: LDAP server root bind password. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_ca_path`: LDAP server certificate authority file name. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_group_search_attr`: LDAP server group search attribute. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_group_search_filter`: LDAP custom group search filter. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_init_pool_size`: LDAP server initial connection pool size. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_log_status`: LDAP server log level. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_max_pool_size`: LDAP server maximum connection pool size. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_referral`: Whether to enable LDAP search referral. Added in MySQL 8.0.20. 
- `authentication_ldap_simple_server_host`: LDAP server host name or IP address. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_server_port`: LDAP server port number. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_tls`: Whether to use encrypted connections to LDAP server. Added in MySQL 8.0.11. 
- `authentication_ldap_simple_user_search_attr`: LDAP server user search attribute. Added in MySQL 8.0.11. 
- `authentication_windows_log_level`: Windows authentication plugin logging level. Added in MySQL 8.0.11. 
- `authentication_windows_use_principal_name`: Whether to use Windows authentication plugin principal name. Added in MySQL 8.0.11. 
- `binlog_encryption`: Enable encryption for binary log files and relay log files on this server. Added in MySQL 8.0.14. 
- `binlog_expire_logs_seconds`: Purge binary logs after this many seconds. Added in MySQL 8.0.1. 
- `binlog_rotate_encryption_master_key_at_startup`: Rotate the binary log master key at server startup. Added in MySQL 8.0.14. 
- `binlog_row_metadata`: Configures the amount of table related metadata binary logged when using row-based logging. Added in MySQL 8.0.1. 
- `binlog_row_value_options`: Enables binary logging of partial JSON updates for row-based replication. Added in MySQL 8.0.3. 
- `binlog_transaction_compression`: Enable compression for transaction payloads in binary log files. Added in MySQL 8.0.20. 
- `binlog_transaction_compression_level_zstd`: Compression level for transaction payloads in binary log files. Added in MySQL 8.0.20. 
- `binlog_transaction_dependency_history_size`: Number of row hashes kept for looking up transaction that last updated some row. Added in MySQL 8.0.1. 
- `binlog_transaction_dependency_tracking`: Source of dependency information (commit timestamps or transaction write sets) from which to assess which transactions can be executed in parallel by slave's multithreaded applier. Added in MySQL 8.0.1. 
- `caching_sha2_password_auto_generate_rsa_keys`: Whether to autogenerate RSA key-pair files. Added in MySQL 8.0.4. 
- `caching_sha2_password_private_key_path`: SHA2 authentication plugin private key path name. Added in MySQL 8.0.3. 
- `caching_sha2_password_public_key_path`: SHA2 authentication plugin public key path name. Added in MySQL 8.0.3. 
- `clone_autotune_concurrency`: Enables dynamic spawning of threads for remote cloning operations. Added in MySQL 8.0.17. 
- `clone_buffer_size`: Defines the size of the intermediate buffer on the donor MySQL server instance. Added in MySQL 8.0.17. 
- `clone_ddl_timeout`: The number of seconds that a cloning operation waits for backup lock. Added in MySQL 8.0.17. 
- `clone_enable_compression`: Enables compression of data at the network layer during cloning. Added in MySQL 8.0.17. 
- `clone_max_concurrency`: The maximum number of concurrent threads used to perform cloning operation. Added in MySQL 8.0.17. 
- `clone_max_data_bandwidth`: The maximum data transfer rate in MiB per second for a remote cloning operation. Added in MySQL 8.0.17. 
- `clone_max_network_bandwidth`: The maximum network transfer rate in MiB per second for a remote cloning operation. Added in MySQL 8.0.17. 
- `clone_ssl_ca`: Specifies the path to the certificate authority (CA) file. Added in MySQL 8.0.14. 
- `clone_ssl_cert`: Specifies the path to the public key certificate file. Added in MySQL 8.0.14. 
- `clone_ssl_key`: Specifies the path to the private key file. Added in MySQL 8.0.14. 
- `clone_valid_donor_list`: Defines donor host addresses for remote cloning operations. Added in MySQL 8.0.17. 
- `connection_control_failed_connections_threshold`: Consecutive failed connection attempts before delays occur. Added in MySQL 8.0.1. 
- `connection_control_max_connection_delay`: Maximum delay (milliseconds) for server response to failed connection attempts. Added in MySQL 8.0.1. 
- `connection_control_min_connection_delay`: Minimum delay (milliseconds) for server response to failed connection attempts. Added in MySQL 8.0.1. 
- `create_admin_listener_thread`: Whether to use dedicated listening thread for connections on administrative interface. Added in MySQL 8.0.14. 
- `cte_max_recursion_depth`: Common table expression maximum recursion depth. Added in MySQL 8.0.3. 
- `ddl-rewriter`: Whether to activate the ddl_rewriter plugin. Added in MySQL 8.0.16. 
- `default_collation_for_utf8mb4`: Default collation for utf8mb4 character set. Added in MySQL 8.0.11. 
- `default_table_encryption`: The default schema and tablespace encryption setting. Added in MySQL 8.0.16. 
- `dragnet.Status`: Result of most recent assignment to dragnet.log_error_filter_rules. Added in MySQL 8.0.12. 
- `dragnet.log_error_filter_rules`: Filter rules for error logging. Added in MySQL 8.0.4. 
- `early-plugin-load`: Specify plugins to load before loading mandatory built-in plugins and before storage engine initialization. Added in MySQL 8.0.0. 
- `generated_random_password_length`: Maximum length of generated passwords. Added in MySQL 8.0.18. 
- `group_replication_advertise_recovery_endpoints`: Connections offered for distributed recovery. Added in MySQL 8.0.21. 
- `group_replication_autorejoin_tries`: Number of tries that a member makes to automatically rejoin the group. Added in MySQL 8.0.16. 
- `group_replication_clone_threshold`: The transaction number gap between the donor and recipient above which a remote cloning operation is used for state transfer. Added in MySQL 8.0.17. 
- `group_replication_communication_debug_options`: The level of debugging messages for Group Replication components. Added in MySQL 8.0.3. 
- `group_replication_communication_max_message_size`: Maximum message size for Group Replication communications, larger messages are fragmented. Added in MySQL 8.0.16. 
- `group_replication_consistency`: The type of transaction consistency guarantee which the group provides. Added in MySQL 8.0.14. 
- `group_replication_exit_state_action`: How the instance behaves when it leaves the group involuntarily. Added in MySQL 8.0.12. 
- `group_replication_flow_control_hold_percent`: Defines what percentage of the group quota remains unused. Added in MySQL 8.0.2. 
- `group_replication_flow_control_max_commit_quota`: Defines the maximum flow control quota of the group. Added in MySQL 8.0.2. 
- `group_replication_flow_control_member_quota_percent`: Defines the percentage of the quota that a member should assume is available for itself when calculating the quotas. Added in MySQL 8.0.2. 
- `group_replication_flow_control_min_quota`: Controls the lowest flow control quota that can be assigned to a member. Added in MySQL 8.0.2. 
- `group_replication_flow_control_min_recovery_quota`: Controls the lowest quota that can be assigned to a member because of another recovering member in the group. Added in MySQL 8.0.2. 
- `group_replication_flow_control_period`: Defines how many seconds to wait between flow control iterations. Added in MySQL 8.0.2. 
- `group_replication_flow_control_release_percent`: Defines how the group quota should be released when flow control no longer needs to throttle the writer members. Added in MySQL 8.0.2. 
- `group_replication_member_expel_timeout`: The time between a suspected failure of a group member and it being expelled from the group, causing a group membership reconfiguration. Added in MySQL 8.0.13. 
- `group_replication_member_weight`: Chance of this member being elected as primary. Added in MySQL 8.0.2. 
- `group_replication_message_cache_size`: Maximum memory for the message cache in the group communication engine (XCom). Added in MySQL 8.0.16. 
- `group_replication_recovery_compression_algorithm`: Permitted compression algorithms for outgoing recovery connections. Added in MySQL 8.0.18. 
- `group_replication_recovery_get_public_key`: Whether to accept preference about fetching public key from master. Added in MySQL 8.0.4. 
- `group_replication_recovery_public_key_path`: To accept public key information. Added in MySQL 8.0.4. 
- `group_replication_recovery_tls_ciphersuites`: Permitted ciphersuites when TLSv1.3 is used for connection encryption with this instance as the client (joining member). Added in MySQL 8.0.19. 
- `group_replication_recovery_tls_version`: Permitted TLS protocols for connection encryption as the client (joining member). Added in MySQL 8.0.19. 
- `group_replication_recovery_zstd_compression_level`: Compression level for recovery connections that use zstd compression. Added in MySQL 8.0.18. 
- `group_replication_tls_source`: Source of TLS material for Group Replication. Added in MySQL 8.0.21. 
- `group_replication_unreachable_majority_timeout`: How long to wait for network partitions that result in a minority to leave the group. Added in MySQL 8.0.2. 
- `histogram_generation_max_mem_size`: Maximum memory for creating histogram statistics. Added in MySQL 8.0.2. 
- `immediate_server_version`: The MySQL Server release number of the server that is the immediate master in a replication topology. Added in MySQL 8.0.14. 
- `information_schema_stats_expiry`: Expiration setting for cached table statistics. Added in MySQL 8.0.3. 
- `innodb_buffer_pool_debug`: Permits multiple buffer pool instances when the buffer pool is less than 1GB in size. Added in MySQL 8.0.0. 
- `innodb_buffer_pool_in_core_file`: Controls writing of buffer pool pages to core files. Added in MySQL 8.0.14. 
- `innodb_checkpoint_disabled`: Disables checkpoints so that a deliberate server exit always initiates recovery. Added in MySQL 8.0.2. 
- `innodb_ddl_log_crash_reset_debug`: A debug option that resets DDL log crash injection counters. Added in MySQL 8.0.3. 
- `innodb_deadlock_detect`: Enables or disables deadlock detection. Added in MySQL 8.0.0. 
- `innodb_dedicated_server`: Enables automatic configuration of buffer pool size, log file size, and flush method. Added in MySQL 8.0.3. 
- `innodb_directories`: Defines directories to scan at startup for tablespace data files. Added in MySQL 8.0.4. 
- `innodb_doublewrite_batch_size`: Number of doublewrite pages to write in a batch. Added in MySQL 8.0.20. 
- `innodb_doublewrite_dir`: Doublewrite buffer file directory. Added in MySQL 8.0.20. 
- `innodb_doublewrite_files`: Number of doublewrite files. Added in MySQL 8.0.20. 
- `innodb_doublewrite_pages`: Number of doublewrite pages per thread. Added in MySQL 8.0.20. 
- `innodb_fsync_threshold`: Controls how often InnoDB calls fsync when creating a new file. Added in MySQL 8.0.13. 
- `innodb_idle_flush_pct`: Limits I/0 operations when InnoDB is idle. Added in MySQL 8.0.18. 
- `innodb_log_checkpoint_fuzzy_now`: A debug option that forces InnoDB to write a fuzzy checkpoint. Added in MySQL 8.0.13. 
- `innodb_log_spin_cpu_abs_lwm`: Minimum amount of CPU usage below which user threads no longer spin while waiting for flushed redo. Added in MySQL 8.0.11. 
- `innodb_log_spin_cpu_pct_hwm`: Maximum amount of CPU usage above which user threads no longer spin while waiting for flushed redo. Added in MySQL 8.0.11. 
- `innodb_log_wait_for_flush_spin_hwm`: The maximum average log flush time beyond which user threads no longer spin while waiting for flushed redo. Added in MySQL 8.0.11. 
- `innodb_log_writer_threads`: Enables dedicated log writer threads for writing and flushing redo logs. Added in MySQL 8.0.22. 
- `innodb_parallel_read_threads`: Defines the number of threads for parallel index reads. Added in MySQL 8.0.14. 
- `innodb_print_ddl_logs`: Whether or not to print DDL logs to the error log. Added in MySQL 8.0.3. 
- `innodb_redo_log_archive_dirs`: Labeled redo log archive directories. Added in MySQL 8.0.17. 
- `innodb_redo_log_encrypt`: Controls encryption of redo log data for encrypted tablespaces. Added in MySQL 8.0.1. 
- `innodb_scan_directories`: Defines directories to scan for tablespace files during InnoDB recovery. Added in MySQL 8.0.2. 
- `innodb_spin_wait_pause_multiplier`: Defines a multiplier value used to determine the number of PAUSE instructions in spin-wait loops. Added in MySQL 8.0.16. 
- `innodb_stats_include_delete_marked`: Include delete-marked records when calculating persistent InnoDB statistics. Added in MySQL 8.0.1. 
- `innodb_temp_tablespaces_dir`: Session temporary tablespaces path. Added in MySQL 8.0.13. 
- `innodb_tmpdir`: The directory location for the temporary table files created during online ALTER TABLE operations. Added in MySQL 8.0.0. 
- `innodb_undo_log_encrypt`: Controls encryption of undo log data for encrypted tablespaces. Added in MySQL 8.0.1. 
- `innodb_validate_tablespace_paths`: Enables tablespace path validation at startup. Added in MySQL 8.0.21. 
- `internal_tmp_mem_storage_engine`: Defines the storage to use for internal in-memory temporary tables. Added in MySQL 8.0.2. 
- `keyring-migration-destination`: Key migration destination keyring plugin. Added in MySQL 8.0.4. 
- `keyring-migration-host`: Host name for connecting to running server for key migration. Added in MySQL 8.0.4. 
- `keyring-migration-password`: Password for connecting to running server for key migration. Added in MySQL 8.0.4. 
- `keyring-migration-port`: TCP/IP port number for connecting to running server for key migration. Added in MySQL 8.0.4. 
- `keyring-migration-socket`: Unix socket file or Windows named pipe for connecting to running server for key migration. Added in MySQL 8.0.4. 
- `keyring-migration-source`: Key migration source keyring plugin. Added in MySQL 8.0.4. 
- `keyring-migration-user`: User name for connecting to running server for key migration. Added in MySQL 8.0.4. 
- `keyring_aws_cmk_id`: AWS keyring plugin customer master key ID value. Added in MySQL 8.0.11. 
- `keyring_aws_conf_file`: AWS keyring plugin configuration file location. Added in MySQL 8.0.11. 
- `keyring_aws_data_file`: AWS keyring plugin storage file location. Added in MySQL 8.0.11. 
- `keyring_aws_region`: AWS keyring plugin region. Added in MySQL 8.0.11. 
- `keyring_encrypted_file_data`: keyring_encrypted_file plugin data file. Added in MySQL 8.0.11. 
- `keyring_encrypted_file_password`: keyring_encrypted_file plugin password. Added in MySQL 8.0.11. 
- `keyring_hashicorp_auth_path`: The HashiCorp Vault AppRole authentication path. Added in MySQL 8.0.18. 
- `keyring_hashicorp_ca_path`: Path to the keyring_hashicorp CA file. Added in MySQL 8.0.18. 
- `keyring_hashicorp_caching`: Whether to enable keyring_hashicorp caching. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_auth_path`: The actual keyring_hashicorp_auth_path value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_ca_path`: The actual keyring_hashicorp_ca_path value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_caching`: The actual keyring_hashicorp_caching value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_role_id`: The actual keyring_hashicorp_role_id value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_server_url`: The actual keyring_hashicorp_server_url value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_commit_store_path`: The actual keyring_hashicorp_store_path value in use. Added in MySQL 8.0.18. 
- `keyring_hashicorp_role_id`: The HashiCorp Vault AppRole authentication role ID. Added in MySQL 8.0.18. 
- `keyring_hashicorp_secret_id`: The HashiCorp Vault AppRole authentication secret ID. Added in MySQL 8.0.18. 
- `keyring_hashicorp_server_url`: The HashiCorp Vault server URL. Added in MySQL 8.0.18. 
- `keyring_hashicorp_store_path`: The HashiCorp Vault store path. Added in MySQL 8.0.18. 
- `keyring_okv_conf_dir`: Oracle Key Vault keyring plugin configuration directory. Added in MySQL 8.0.11. 
- `keyring_operations`: Whether keyring operations are enabled. Added in MySQL 8.0.4. 
- `lock_order`: Whether to enable LOCK_ORDER tool at runtime. Added in MySQL 8.0.17. 
- `lock_order_debug_loop`: Whether to cause debug assert when LOCK_ORDER tool encounters dependency flagged as a loop. Added in MySQL 8.0.17. 
- `lock_order_debug_missing_arc`: Whether to cause debug assert when LOCK_ORDER tool encounters undeclared dependency. Added in MySQL 8.0.17. 
- `lock_order_debug_missing_key`: Whether to cause debug assert when LOCK_ORDER tool encounters object not properly instrumented with the Performance Schema. Added in MySQL 8.0.17. 
- `lock_order_debug_missing_unlock`: Whether to cause debug assert when LOCK_ORDER tool encounters lock that is destroyed while still held. Added in MySQL 8.0.17. 
- `lock_order_dependencies`: Path to the lock_order_dependencies.txt file. Added in MySQL 8.0.17. 
- `lock_order_extra_dependencies`: Path to a second dependency file. Added in MySQL 8.0.17. 
- `lock_order_output_directory`: Directory where LOCK_ORDER tool writes logs. Added in MySQL 8.0.17. 
- `lock_order_print_txt`: Whether to perform lock-order graph analysis and print textual report. Added in MySQL 8.0.17. 
- `lock_order_trace_loop`: Whether to print log file trace when LOCK_ORDER tool encounters dependency flagged as a loop. Added in MySQL 8.0.17. 
- `lock_order_trace_missing_arc`: Whether to print log file trace when LOCK_ORDER tool encounters undeclared dependency. Added in MySQL 8.0.17. 
- `lock_order_trace_missing_key`: Whether to print log file trace when LOCK_ORDER tool encounters object not properly instrumented with the Performance Schema. Added in MySQL 8.0.17. 
- `lock_order_trace_missing_unlock`: Whether to print log file trace when LOCK_ORDER tool encounters lock that is destroyed while still held. Added in MySQL 8.0.17. 
- `log_error_filter_rules`: Filter rules for error logging. Added in MySQL 8.0.2. 
- `log_error_services`: Components to use for error logging. Added in MySQL 8.0.2. 
- `log_error_suppression_list`: Warning/information error log messages to suppress. Added in MySQL 8.0.13. 
- `log_slow_extra`: Whether to write extra information to the slow query log file. Added in MySQL 8.0.14. 
- `mandatory_roles`: Automatically granted roles for all users. Added in MySQL 8.0.2. 
- `mysql_firewall_mode`: Whether MySQL Enterprise Firewall is operational. Added in MySQL 8.0.11. 
- `mysql_firewall_trace`: Whether to enable firewall trace. Added in MySQL 8.0.11. 
- `mysqlx`: Whether X Plugin is initialized. Added in MySQL 8.0.11. 
- `mysqlx_compression_algorithms`: Compression algorithms permitted for X Protocol connections. Added in MySQL 8.0.19. 
- `mysqlx_deflate_default_compression_level`: Default compression level for the Deflate algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `mysqlx_deflate_max_client_compression_level`: Maximum permitted compression level for the Deflate algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `mysqlx_interactive_timeout`: Number of seconds to wait for interactive clients to timeout. Added in MySQL 8.0.4. 
- `mysqlx_lz4_default_compression_level`: Default compression level for the LZ4 algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `mysqlx_lz4_max_client_compression_level`: Maximum permitted compression level for the LZ4 algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `mysqlx_read_timeout`: Number of seconds to wait for blocking read operations to complete. Added in MySQL 8.0.4. 
- `mysqlx_wait_timeout`: Number of seconds to wait for activity on a connection. Added in MySQL 8.0.4. 
- `mysqlx_write_timeout`: Number of seconds to wait for blocking write operations to complete. Added in MySQL 8.0.4. 
- `mysqlx_zstd_default_compression_level`: Default compression level for the zstd algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `mysqlx_zstd_max_client_compression_level`: Maximum permitted compression level for the zstd algorithm on X Protocol connections. Added in MySQL 8.0.20. 
- `named_pipe_full_access_group`: Name of Windows group granted full access to the named pipe. Added in MySQL 8.0.14. 
- `no-dd-upgrade`: Prevent automatic upgrade of data dictionary tables at startup. Added in MySQL 8.0.4. 
- `no-monitor`: Do not fork monitor process required for RESTART. Added in MySQL 8.0.12. 
- `original_commit_timestamp`: The time when a transaction was committed on the original master. Added in MySQL 8.0.1. 
- `original_server_version`: The MySQL Server release number of the server where a transaction was originally committed. Added in MySQL 8.0.14. 
- `partial_revokes`: Whether partial revocation is enabled. Added in MySQL 8.0.16. 
- `password_history`: Number of password changes required before password reuse. Added in MySQL 8.0.3. 
- `password_require_current`: Whether password changes require current password verification. Added in MySQL 8.0.13. 
- `password_reuse_interval`: Number of days elapsed required before password reuse. Added in MySQL 8.0.3. 
- `performance_schema_max_digest_sample_age`: The query resample age in seconds. Added in MySQL 8.0.3. 
- `performance_schema_show_processlist`: Select SHOW PROCESSLIST implementation. Added in MySQL 8.0.22. 
- `persist_only_admin_x509_subject`: SSL certificate X.509 Subject that enables persisting persist-restricted system variables. Added in MySQL 8.0.14. 
- `persisted_globals_load`: Whether to load persisted configuration settings. Added in MySQL 8.0.0. 
- `print_identified_with_as_hex`: For SHOW CREATE USER, print hash values containing unprintable characters in hex. Added in MySQL 8.0.17. 
- `protocol_compression_algorithms`: Permitted compression algorithms for incoming connections. Added in MySQL 8.0.18. 
- `regexp_stack_limit`: Regular expression match stack size limit. Added in MySQL 8.0.4. 
- `regexp_time_limit`: Regular expression match timeout. Added in MySQL 8.0.4. 
- `require_row_format`: For internal server use. Added in MySQL 8.0.19. 
- `resultset_metadata`: Whether the server returns result set metadata. Added in MySQL 8.0.3. 
- `rpl_read_size`: Set the minimum amount of data in bytes that is read from the binary log files and relay log files. Added in MySQL 8.0.11. 
- `secondary_engine_cost_threshold`: For future use. Added in MySQL 8.0.16. 
- `show_create_table_skip_secondary_engine`: Whether to exclude the SECONDARY ENGINE clause from SHOW CREATE TABLE output. Added in MySQL 8.0.18. 
- `show_create_table_verbosity`: Whether to display ROW_FORMAT in SHOW CREATE TABLE even if it has the default value. Added in MySQL 8.0.11. 
- `sql_require_primary_key`: Whether tables must have a primary key. Added in MySQL 8.0.13. 
- `ssl_fips_mode`: Whether to enable FIPS mode on server side. Added in MySQL 8.0.11. 
- `syseventlog.facility`: Facility for syslog messages. Added in MySQL 8.0.13. 
- `syseventlog.include_pid`: Whether to include server PID in syslog messages. Added in MySQL 8.0.13. 
- `syseventlog.tag`: Tag for server identifier in syslog messages. Added in MySQL 8.0.13. 
- `table_encryption_privilege_check`: Enables the TABLE_ENCRYPTION_ADMIN privilege check. Added in MySQL 8.0.16. 
- `temptable_max_ram`: Defines the maximum amount of memory that can occupied by the TempTable storage engine before data is stored on disk. Added in MySQL 8.0.2. 
- `temptable_use_mmap`: Defines whether the TempTable storage engine allocates memory-mapped files when the temptable_max_ram threshold is reached. Added in MySQL 8.0.16. 
- `thread_pool_algorithm`: The thread pool algorithm. Added in MySQL 8.0.11. 
- `thread_pool_high_priority_connection`: Whether the current session is high priority. Added in MySQL 8.0.11. 
- `thread_pool_max_active_query_threads`: Maximum permissible number of active query threads per group. Added in MySQL 8.0.19. 
- `thread_pool_max_unused_threads`: Maximum permissible number of unused threads. Added in MySQL 8.0.11. 
- `thread_pool_prio_kickup_timer`: How long before a statement is moved to high-priority execution. Added in MySQL 8.0.11. 
- `thread_pool_size`: Number of thread groups in the thread pool. Added in MySQL 8.0.11. 
- `thread_pool_stall_limit`: How long before a statement is defined as stalled. Added in MySQL 8.0.11. 
- `tls_ciphersuites`: Permissible TLSv1.3 ciphersuites for encrypted connections. Added in MySQL 8.0.16. 
- `upgrade`: Control automatic upgrade at startup. Added in MySQL 8.0.16. 
- `use_secondary_engine`: For future use. Added in MySQL 8.0.13. 
- `validate-config`: Validate server configuration. Added in MySQL 8.0.16. 
- `validate_password.check_user_name`: Whether to check passwords against user name. Added in MySQL 8.0.4. 
- `validate_password.dictionary_file`: validate_password dictionary file. Added in MySQL 8.0.4. 
- `validate_password.dictionary_file_last_parsed`: When the dictionary file was last parsed. Added in MySQL 8.0.4. 
- `validate_password.dictionary_file_words_count`: Number of words in dictionary file. Added in MySQL 8.0.4. 
- `validate_password.length`: validate_password required password length. Added in MySQL 8.0.4. 
- `validate_password.mixed_case_count`: validate_password required number of uppercase/lowercase characters. Added in MySQL 8.0.4. 
- `validate_password.number_count`: validate_password required number of digit characters. Added in MySQL 8.0.4. 
- `validate_password.policy`: validate_password password policy. Added in MySQL 8.0.4. 
- `validate_password.special_char_count`: validate_password required number of special characters. Added in MySQL 8.0.4. 
- `version_compile_zlib`: Version of compiled-in zlib library. Added in MySQL 8.0.11. 
- `windowing_use_high_precision`: Whether to compute window functions to high precision. Added in MySQL 8.0.2.

### Options and Variables Deprecated in MySQL 8.0

​ The following system variables, status variables, and options have been deprecated in MySQL 8.0.



- `Compression`: Whether the client connection uses compression in the client/server protocol. Deprecated as of MySQL 8.0.18. 
- `expire_logs_days`: Purge binary logs after this many days. Deprecated as of MySQL 8.0.3. 
- `innodb_undo_tablespaces`: Number of tablespace files that rollback segments are divided between. Deprecated as of MySQL 8.0.4. 
- `log_bin_use_v1_row_events`: Whether server is using version 1 binary log row events. Deprecated as of MySQL 8.0.18. 
- `log_syslog`: Whether to write error log to syslog. Deprecated as of MySQL 8.0.2. 
- `master-info-file`: The location and name of the file that remembers the master and where the I/O replication thread is in the master's binary logs. Deprecated as of MySQL 8.0.18. 
- `max_length_for_sort_data`: Max number of bytes in sorted records. Deprecated as of MySQL 8.0.20. 
- `no-dd-upgrade`: Prevent automatic upgrade of data dictionary tables at startup. Deprecated as of MySQL 8.0.16. 
- `relay_log_info_file`: File in which the slave records information about the relay logs. Deprecated as of MySQL 8.0.18. 
- `slave_compressed_protocol`: Use compression of master/slave protocol. Deprecated as of MySQL 8.0.18. 
- `slave_rows_search_algorithms`: Determines search algorithms used for slave update batching. Any 2 or 3 from the list INDEX_SEARCH, TABLE_SCAN, HASH_SCAN. Deprecated as of MySQL 8.0.18. 
- `symbolic-links`: Permit symbolic links for MyISAM tables. Deprecated as of MySQL 8.0.2.

### Options and Variables Removed in MySQL 8.0

​ The following system variables, status variables, and options have been removed in MySQL 8.0.



- `Com_alter_db_upgrade`: Count of ALTER DATABASE ... UPGRADE DATA DIRECTORY NAME statements. Removed in MySQL 8.0.0. 
- `Innodb_available_undo_logs`: Display the total number of InnoDB rollback segments; different from innodb_rollback_segments, which displays the number of active rollback segments. Removed in MySQL 8.0.2. 
- `Qcache_free_blocks`: Number of free memory blocks in the query cache. Removed in MySQL 8.0.3. 
- `Qcache_free_memory`: The amount of free memory for the query cache. Removed in MySQL 8.0.3. 
- `Qcache_hits`: Number of query cache hits. Removed in MySQL 8.0.3. 
- `Qcache_inserts`: Number of query cache inserts. Removed in MySQL 8.0.3. 
- `Qcache_lowmem_prunes`: Number of queries that were deleted from the query cache due to lack of free memory in the cache. Removed in MySQL 8.0.3. 
- `Qcache_not_cached`: Number of noncached queries (not cacheable, or not cached due to the query_cache_type setting). Removed in MySQL 8.0.3. 
- `Qcache_queries_in_cache`: Number of queries registered in the query cache. Removed in MySQL 8.0.3. 
- `Qcache_total_blocks`: The total number of blocks in the query cache. Removed in MySQL 8.0.3. 
- `Slave_heartbeat_period`: The slave's replication heartbeat interval, in seconds. Removed in MySQL 8.0.1. 
- `Slave_last_heartbeat`: Shows when the latest heartbeat signal was received, in TIMESTAMP format. Removed in MySQL 8.0.1. 
- `Slave_received_heartbeats`: Number of heartbeats received by a replication slave since previous reset. Removed in MySQL 8.0.1. 
- `Slave_retried_transactions`: The total number of times since startup that the replication slave SQL thread has retried transactions. Removed in MySQL 8.0.1. 
- `Slave_running`: The state of this server as a replication slave (slave I/O thread status). Removed in MySQL 8.0.1. 
- `bootstrap`: Used by mysql installation scripts. Removed in MySQL 8.0.0. 
- `date_format`: The DATE format (unused). Removed in MySQL 8.0.3. 
- `datetime_format`: The DATETIME/TIMESTAMP format (unused). Removed in MySQL 8.0.3. 
- `des-key-file`: Load keys for des_encrypt() and des_encrypt from given file. Removed in MySQL 8.0.3. 
- `group_replication_allow_local_disjoint_gtids_join`: Allow the current server to join the group even if it has transactions not present in the group. Removed in MySQL 8.0.4. 
- `have_crypt`: Availability of the crypt() system call. Removed in MySQL 8.0.3. 
- `ignore-db-dir`: Treat directory as nondatabase directory. Removed in MySQL 8.0.0. 
- `ignore_builtin_innodb`: Ignore the built-in InnoDB. Removed in MySQL 8.0.3. 
- `ignore_db_dirs`: Directories treated as nondatabase directories. Removed in MySQL 8.0.0. 
- `innodb_checksums`: Enable InnoDB checksums validation. Removed in MySQL 8.0.0. 
- `innodb_disable_resize_buffer_pool_debug`: Disables resizing of the InnoDB buffer pool. Removed in MySQL 8.0.0. 
- `innodb_file_format`: The format for new InnoDB tables. Removed in MySQL 8.0.0. 
- `innodb_file_format_check`: Whether InnoDB performs file format compatibility checking. Removed in MySQL 8.0.0. 
- `innodb_file_format_max`: The file format tag in the shared tablespace. Removed in MySQL 8.0.0. 
- `innodb_large_prefix`: Enables longer keys for column prefix indexes. Removed in MySQL 8.0.0. 
- `innodb_locks_unsafe_for_binlog`: Force InnoDB not to use next-key locking. Instead use only row-level locking. Removed in MySQL 8.0.0. 
- `innodb_scan_directories`: Defines directories to scan for tablespace files during InnoDB recovery. Removed in MySQL 8.0.4. 
- `innodb_stats_sample_pages`: Number of index pages to sample for index distribution statistics. Removed in MySQL 8.0.0. 
- `innodb_support_xa`: Enable InnoDB support for the XA two-phase commit. Removed in MySQL 8.0.0. 
- `innodb_undo_logs`: Defines the number of undo logs (rollback segments) used by InnoDB; an alias for innodb_rollback_segments. Removed in MySQL 8.0.2. 
- `internal_tmp_disk_storage_engine`: Storage engine for internal temporary tables. Removed in MySQL 8.0.16. 
- `log-warnings`: Log some noncritical warnings to the log file. Removed in MySQL 8.0.3. 
- `log_builtin_as_identified_by_password`: Whether to log CREATE/ALTER USER, GRANT in backward-compatible fashion. Removed in MySQL 8.0.11. 
- `log_error_filter_rules`: Filter rules for error logging. Removed in MySQL 8.0.4. 
- `log_syslog`: Whether to write error log to syslog. Removed in MySQL 8.0.13. 
- `log_syslog_facility`: Facility for syslog messages. Removed in MySQL 8.0.13. 
- `log_syslog_include_pid`: Whether to include server PID in syslog messages. Removed in MySQL 8.0.13. 
- `log_syslog_tag`: Tag for server identifier in syslog messages. Removed in MySQL 8.0.13. 
- `max_tmp_tables`: Unused. Removed in MySQL 8.0.3. 
- `metadata_locks_cache_size`: Size of the metadata locks cache. Removed in MySQL 8.0.13. 
- `metadata_locks_hash_instances`: Number of metadata lock hashes. Removed in MySQL 8.0.13. 
- `multi_range_count`: The maximum number of ranges to send to a table handler at once during range selects. Removed in MySQL 8.0.3. 
- `old_passwords`: Selects password hashing method for PASSWORD(). Removed in MySQL 8.0.11. 
- `partition`: Enable (or disable) partitioning support. Removed in MySQL 8.0.0. 
- `query_cache_limit`: Do not cache results that are bigger than this. Removed in MySQL 8.0.3. 
- `query_cache_min_res_unit`: Minimal size of unit in which space for results is allocated (last unit will be trimmed after writing all result data). Removed in MySQL 8.0.3. 
- `query_cache_size`: The memory allocated to store results from old queries. Removed in MySQL 8.0.3. 
- `query_cache_type`: Query cache type. Removed in MySQL 8.0.3. 
- `query_cache_wlock_invalidate`: Invalidate queries in query cache on LOCK for write. Removed in MySQL 8.0.3. 
- `secure_auth`: Disallow authentication for accounts that have old (pre-4.1) passwords. Removed in MySQL 8.0.3. 
- `show_compatibility_56`: Compatibility for SHOW STATUS/VARIABLES. Removed in MySQL 8.0.1. 
- `skip-partition`: Do not enable user-defined partitioning. Removed in MySQL 8.0.0. 
- `sync_frm`: Sync .frm to disk on create. Enabled by default. Removed in MySQL 8.0.0. 
- `temp-pool`: Using this option will cause most temporary files created to use a small set of names, rather than a unique name for each new file. Removed in MySQL 8.0.1. 
- `time_format`: The TIME format (unused). Removed in MySQL 8.0.3. 
- `tx_isolation`: The default transaction isolation level. Removed in MySQL 8.0.3. 
- `tx_read_only`: Default transaction access mode. Removed in MySQL 8.0.3.

## 1.6 MySQL Information Sources

- [1.6.1 MySQL Websites](#mysql-web-sites)
- [1.6.2 MySQL Community Support at the MySQL Forums](#forums)
- [1.6.3 MySQL Enterprise](#mysql-enterprise-information)

​ This section lists sources of additional information that you may find helpful, such as MySQL websites, mailing lists, user forums, and Internet Relay Chat.

### 1.6.1 MySQL Websites



​ The primary website for MySQL documentation is https://dev.mysql.com/doc/. Online and downloadable documentation formats are available for the MySQL Reference Manual, MySQL Connectors, and more. 

​ The MySQL developers provide information about new and upcoming features as the [MySQL Server Blog](http://mysqlserverteam.com/).

### 1.6.2 MySQL Community Support at the MySQL Forums



​ The forums at http://forums.mysql.com are an important community resource. Many forums are available, grouped into these general categories:

- Migration 
- MySQL Usage 
- MySQL Connectors 
- Programming Languages 
- Tools 
- 3rd-Party Applications 
- Storage Engines 
- MySQL Technology 
- SQL Standards 
- Business

### 1.6.3 MySQL Enterprise

​ Oracle offers technical support in the form of MySQL Enterprise. For organizations that rely on the MySQL DBMS for business-critical production applications, MySQL Enterprise is a commercial subscription offering which includes:

-  MySQL Enterprise Server 
-  MySQL Enterprise Monitor 
-  Monthly Rapid Updates and Quarterly Service Packs 
-  MySQL Knowledge Base 
-  24x7 Technical and Consultative Support

​ MySQL Enterprise is available in multiple tiers, giving you the flexibility to choose the level of service that best matches your needs. For more information, see [MySQL Enterprise](https://www.mysql.com/products/enterprise/).

## 1.7 How to Report Bugs or Problems



​ Before posting a bug report about a problem, please try to verify that it is a bug and that it has not been reported already:

- Start by searching the MySQL online manual at https://dev.mysql.com/doc/. We try to keep the manual up to date by updating it frequently with solutions to newly found problems. In addition, the release notes accompanying the manual can be particularly useful since it is quite possible that a newer version contains a solution to your problem. The release notes are available at the location just given for the manual. 

- If you get a parse error for an SQL statement, please check your syntax closely. If you cannot find something wrong with it, it is extremely likely that your current version of MySQL Server doesn't support the syntax you are using. If you are using the current version and the manual doesn't cover the syntax that you are using, MySQL Server doesn't support your statement. 

 ​ If the manual covers the syntax you are using, but you have an older version of MySQL Server, you should check the MySQL change history to see when the syntax was implemented. In this case, you have the option of upgrading to a newer version of MySQL Server. 

- For solutions to some common problems, see [Section B.3, “Problems and Common Errors”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/error-handling.html#problems). 

- Search the bugs database at http://bugs.mysql.com/ to see whether the bug has been reported and fixed. 

- You can also use http://www.mysql.com/search/ to search all the Web pages (including the manual) that are located at the MySQL website.

​ If you cannot find an answer in the manual, the bugs database, or the mailing list archives, check with your local MySQL expert. If you still cannot find an answer to your question, please use the following guidelines for reporting the bug. 

​ The normal way to report bugs is to visit http://bugs.mysql.com/, which is the address for our bugs database. This database is public and can be browsed and searched by anyone. If you log in to the system, you can enter new reports. 

​ Bugs posted in the bugs database at http://bugs.mysql.com/ that are corrected for a given release are noted in the release notes. 

​ If you find a security bug in MySQL Server, please let us know immediately by sending an email message to `<secalert_us@oracle.com>`. Exception: Support customers should report all problems, including security bugs, to Oracle Support at http://support.oracle.com/. 

​ To discuss problems with other users, you can use the [MySQL Community  Slack](https://mysqlcommunity.slack.com/). 

​ Writing a good bug report takes patience, but doing it right the first time saves time both for us and for yourself. A good bug report, containing a full test case for the bug, makes it very likely that we will fix the bug in the next release. This section helps you write your report correctly so that you do not waste your time doing things that may not help us much or at all. Please read this section carefully and make sure that all the information described here is included in your report. 

​ Preferably, you should test the problem using the latest production or development version of MySQL Server before posting. Anyone should be able to repeat the bug by just using `mysql test < script_file` on your test case or by running the shell or Perl script that you include in the bug report. Any bug that we are able to repeat has a high chance of being fixed in the next MySQL release. 

​ It is most helpful when a good description of the problem is included in the bug report. That is, give a good example of everything you did that led to the problem and describe, in exact detail, the problem itself. The best reports are those that include a full example showing how to reproduce the bug or problem. See [Section 29.5, “Debugging and Porting MySQL”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/extending-mysql.html#porting). 

​ Remember that it is possible for us to respond to a report containing too much information, but not to one containing too little. People often omit facts because they think they know the cause of a problem and assume that some details do not matter. A good principle to follow is that if you are in doubt about stating something, state it. It is faster and less troublesome to write a couple more lines in your report than to wait longer for the answer if we must ask you to provide information that was missing from the initial report. 

​ The most common errors made in bug reports are (a) not including the version number of the MySQL distribution that you use, and (b) not fully describing the platform on which the MySQL server is installed (including the platform type and version number). These are highly relevant pieces of information, and in 99 cases out of 100, the bug report is useless without them. Very often we get questions like, “Why doesn't this work for me?” Then we find that the feature requested wasn't implemented in that MySQL version, or that a bug described in a report has been fixed in newer MySQL versions. Errors often are platform-dependent. In such cases, it is next to impossible for us to fix anything without knowing the operating system and the version number of the platform. 

​ If you compiled MySQL from source, remember also to provide information about your compiler if it is related to the problem. Often people find bugs in compilers and think the problem is MySQL-related. Most compilers are under development all the time and become better version by version. To determine whether your problem depends on your compiler, we need to know what compiler you used. Note that every compiling problem should be regarded as a bug and reported accordingly. 

​ If a program produces an error message, it is very important to include the message in your report. If we try to search for something from the archives, it is better that the error message reported exactly matches the one that the program produces. (Even the lettercase should be observed.) It is best to copy and paste the entire error message into your report. You should never try to reproduce the message from memory. 

​ If you have a problem with Connector/ODBC (MyODBC), please try to generate a trace file and send it with your report. See [How to Report Connector/ODBC Problems or Bugs](https://dev.mysql.com/doc/connector-odbc/en/connector-odbc-support-bug-report.html). 

​ If your report includes long query output lines from test cases that you run with the [**mysql**](programs#mysql) command-line tool, you can make the output more readable by using the [`--vertical`](programs#option_mysql_vertical) option or the `\G` statement terminator. The [`EXPLAIN SELECT`](sql-statements.html#explain) example later in this section demonstrates the use of `\G`. 

​ Please include the following information in your report:

- The version number of the MySQL distribution you are using (for example, MySQL 5.7.10). You can find out which version you are running by executing [**mysqladmin version**](programs#mysqladmin). The [**mysqladmin**](programs#mysqladmin) program can be found in the `bin` directory under your MySQL installation directory. 

- The manufacturer and model of the machine on which you experience the problem. 

- The operating system name and version. If you work with Windows, you can usually get the name and version number by double-clicking your My Computer icon and pulling down the “Help/About Windows” menu. For most Unix-like operating systems, you can get this information by executing the command `uname -a`. 

- Sometimes the amount of memory (real and virtual) is relevant. If in doubt, include these values. 

- The contents of the `docs/INFO_BIN` file from your MySQL installation. This file contains information about how MySQL was configured and compiled. 

 

- If you are using a source distribution of the MySQL software, include the name and version number of the compiler that you used. If you have a binary distribution, include the distribution name. 

- If the problem occurs during compilation, include the exact error messages and also a few lines of context around the offending code in the file where the error occurs. 

- If [**mysqld**](programs#mysqld) died, you should also report the statement that crashed [**mysqld**](programs#mysqld). You can usually get this information by running [**mysqld**](programs#mysqld) with query logging enabled, and then looking in the log after [**mysqld**](programs#mysqld) crashes. See [Section 29.5, “Debugging and Porting MySQL”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/extending-mysql.html#porting). 

- If a database table is related to the problem, include the output from the `SHOW CREATE TABLE *`db_name`*.*`tbl_name`*` statement in the bug report. This is a very easy way to get the definition of any table in a database. The information helps us create a situation matching the one that you have experienced. 

- The SQL mode in effect when the problem occurred can be significant, so please report the value of the [`sql_mode`](server-administration#sysvar_sql_mode) system variable. For stored procedure, stored function, and trigger objects, the relevant [`sql_mode`](server-administration#sysvar_sql_mode) value is the one in effect when the object was created. For a stored procedure or function, the [`SHOW CREATE PROCEDURE`](sql-statements.html#show-create-procedure) or [`SHOW CREATE FUNCTION`](sql-statements.html#show-create-function) statement shows the relevant SQL mode, or you can query `INFORMATION_SCHEMA` for the information: 

 ```
 SELECT ROUTINE_SCHEMA, ROUTINE_NAME, SQL_MODE
 FROM INFORMATION_SCHEMA.ROUTINES;
 ```

 ​ For triggers, you can use this statement: 

 ```
 SELECT EVENT_OBJECT_SCHEMA, EVENT_OBJECT_TABLE, TRIGGER_NAME, SQL_MODE
 FROM INFORMATION_SCHEMA.TRIGGERS;
 ```

- For performance-related bugs or problems with [`SELECT`](sql-statements.html#select) statements, you should always include the output of `EXPLAIN SELECT ...`, and at least the number of rows that the [`SELECT`](sql-statements.html#select) statement produces. You should also include the output from `SHOW CREATE TABLE *`tbl_name`*` for each table that is involved. The more information you provide about your situation, the more likely it is that someone can help you. 

 ​ The following is an example of a very good bug report. The statements are run using the [**mysql**](programs#mysql) command-line tool. Note the use of the `\G` statement terminator for statements that would otherwise provide very long output lines that are difficult to read. 

 ```
 mysql> SHOW VARIABLES;
 mysql> SHOW COLUMNS FROM ...\G
 <output from SHOW COLUMNS>
 mysql> EXPLAIN SELECT ...\G
 <output from EXPLAIN>
 mysql> FLUSH STATUS;
 mysql> SELECT ...;
 <A short version of the output from SELECT,
 including the time taken to run the query>
 mysql> SHOW STATUS;
 <output from SHOW STATUS>
 ```

- If a bug or problem occurs while running [**mysqld**](programs#mysqld), try to provide an input script that reproduces the anomaly. This script should include any necessary source files. The more closely the script can reproduce your situation, the better. If you can make a reproducible test case, you should upload it to be attached to the bug report. 

 ​ If you cannot provide a script, you should at least include the output from [**mysqladmin variables extended-status processlist**](programs#mysqladmin) in your report to provide some information on how your system is performing. 

- If you cannot produce a test case with only a few rows, or if the test table is too big to be included in the bug report (more than 10 rows), you should dump your tables using [**mysqldump**](programs#mysqldump) and create a `README` file that describes your problem. Create a compressed archive of your files using **tar** and **gzip** or **zip**. After you initiate a bug report for our bugs database at http://bugs.mysql.com/, click the Files tab in the bug report for instructions on uploading the archive to the bugs database. 

- If you believe that the MySQL server produces a strange result from a statement, include not only the result, but also your opinion of what the result should be, and an explanation describing the basis for your opinion. 

- When you provide an example of the problem, it is better to use the table names, variable names, and so forth that exist in your actual situation than to come up with new names. The problem could be related to the name of a table or variable. These cases are rare, perhaps, but it is better to be safe than sorry. After all, it should be easier for you to provide an example that uses your actual situation, and it is by all means better for us. If you have data that you do not want to be visible to others in the bug report, you can upload it using the Files tab as previously described. If the information is really top secret and you do not want to show it even to us, go ahead and provide an example using other names, but please regard this as the last choice. 

- Include all the options given to the relevant programs, if possible. For example, indicate the options that you use when you start the [**mysqld**](programs#mysqld) server, as well as the options that you use to run any MySQL client programs. The options to programs such as [**mysqld**](programs#mysqld) and [**mysql**](programs#mysql), and to the **configure** script, are often key to resolving problems and are very relevant. It is never a bad idea to include them. If your problem involves a program written in a language such as Perl or PHP, please include the language processor's version number, as well as the version for any modules that the program uses. For example, if you have a Perl script that uses the `DBI` and `DBD::mysql` modules, include the version numbers for Perl, `DBI`, and `DBD::mysql`. 

- If your question is related to the privilege system, please include the output of [**mysqladmin reload**](programs#mysqladmin), and all the error messages you get when trying to connect. When you test your privileges, you should execute [**mysqladmin reload version**](programs#mysqladmin) and try to connect with the program that gives you trouble. 

- If you have a patch for a bug, do include it. But do not assume that the patch is all we need, or that we can use it, if you do not provide some necessary information such as test cases showing the bug that your patch fixes. We might find problems with your patch or we might not understand it at all. If so, we cannot use it. 

 ​ If we cannot verify the exact purpose of the patch, we will not use it. Test cases help us here. Show that the patch handles all the situations that may occur. If we find a borderline case (even a rare one) where the patch will not work, it may be useless. 

- Guesses about what the bug is, why it occurs, or what it depends on are usually wrong. Even the MySQL team cannot guess such things without first using a debugger to determine the real cause of a bug. 

- Indicate in your bug report that you have checked the reference manual and mail archive so that others know you have tried to solve the problem yourself. 

- If your data appears corrupt or you get errors when you access a particular table, first check your tables with [`CHECK TABLE`](sql-statements.html#check-table). If that statement reports any errors:

 -  The `InnoDB` crash recovery mechanism  handles cleanup when the server is restarted after being  killed, so in typical operation there is no need to  “repair” tables. If you encounter an error with  `InnoDB` tables, restart the server and see  whether the problem persists, or whether the error affected  only cached data in memory. If data is corrupted on disk,  consider restarting with the  [`innodb_force_recovery`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html#sysvar_innodb_force_recovery)  option enabled so that you can dump the affected tables. 
 -  For non-transactional tables, try to repair them with  [`REPAIR TABLE`](sql-statements.html#repair-table) or with  [**myisamchk**](programs#myisamchk). See  [Chapter 5, *MySQL Server Administration*](server-administration).

 ​ If you are running Windows, please verify the value of [`lower_case_table_names`](server-administration#sysvar_lower_case_table_names) using the `SHOW VARIABLES LIKE 'lower_case_table_names'` statement. This variable affects how the server handles lettercase of database and table names. Its effect for a given value should be as described in [Section 9.2.3, “Identifier Case Sensitivity”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/language-structure.html#identifier-case-sensitivity). 

- If you often get corrupted tables, you should try to find out when and why this happens. In this case, the error log in the MySQL data directory may contain some information about what happened. (This is the file with the `.err` suffix in the name.) See [Section 5.4.2, “The Error Log”](server-administration#error-log). Please include any relevant information from this file in your bug report. Normally [**mysqld**](programs#mysqld) should *never* crash a table if nothing killed it in the middle of an update. If you can find the cause of [**mysqld**](programs#mysqld) dying, it is much easier for us to provide you with a fix for the problem. See [Section B.3.1, “How to Determine What Is Causing a Problem”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/error-handling.html#what-is-crashing). 

- If possible, download and install the most recent version of MySQL Server and check whether it solves your problem. All versions of the MySQL software are thoroughly tested and should work without problems. We believe in making everything as backward-compatible as possible, and you should be able to switch MySQL versions without difficulty. See [Section 2.1.1, “Which MySQL Version and Distribution to Install”](installing#which-version).

## 1.8 MySQL Standards Compliance

- [1.8.1 MySQL Extensions to Standard SQL](#extensions-to-ansi)
- [1.8.2 MySQL Differences from Standard SQL](#differences-from-ansi)
- [1.8.3 How MySQL Deals with Constraints](#constraints)



​ This section describes how MySQL relates to the ANSI/ISO SQL standards. MySQL Server has many extensions to the SQL standard, and here you can find out what they are and how to use them. You can also find information about functionality missing from MySQL Server, and how to work around some of the differences. 

​ The SQL standard has been evolving since 1986 and several versions exist. In this manual, “SQL-92” refers to the standard released in 1992. “SQL:1999”, “SQL:2003”, “SQL:2008”, and “SQL:2011” refer to the versions of the standard released in the corresponding years, with the last being the most recent version. We use the phrase “the SQL standard” or “standard SQL” to mean the current version of the SQL Standard at any time. 

​ One of our main goals with the product is to continue to work toward compliance with the SQL standard, but without sacrificing speed or reliability. We are not afraid to add extensions to SQL or support for non-SQL features if this greatly increases the usability of MySQL Server for a large segment of our user base. The [`HANDLER`](sql-statements.html#handler) interface is an example of this strategy. See [Section 13.2.4, “HANDLER Statement”](sql-statements.html#handler). 

​ We continue to support transactional and nontransactional databases to satisfy both mission-critical 24/7 usage and heavy Web or logging usage. 

​ MySQL Server was originally designed to work with medium-sized databases (10-100 million rows, or about 100MB per table) on small computer systems. Today MySQL Server handles terabyte-sized databases. 

​ We are not targeting real-time support, although MySQL replication capabilities offer significant functionality. 

​ MySQL supports ODBC levels 0 to 3.51. 

​ MySQL supports high-availability database clustering using the [`NDBCLUSTER`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html) storage engine. See [Chapter 22, *MySQL NDB Cluster 8.0*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html). 

​ We implement XML functionality which supports most of the W3C XPath standard. See [Section 12.11, “XML Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#xml-functions). 

​ MySQL supports a native JSON data type as defined by RFC 7159, and based on the ECMAScript standard (ECMA-262). See [Section 11.5, “The JSON Data Type”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#json). MySQL also implements a subset of the SQL/JSON functions specified by a pre-publication draft of the SQL:2016 standard; see [Section 12.17, “JSON Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#json-functions), for more information.

### Selecting SQL Modes

​ The MySQL server can operate in different SQL modes, and can apply these modes differently for different clients, depending on the value of the [`sql_mode`](server-administration#sysvar_sql_mode) system variable. DBAs can set the global SQL mode to match site server operating requirements, and each application can set its session SQL mode to its own requirements. 

​ Modes affect the SQL syntax MySQL supports and the data validation checks it performs. This makes it easier to use MySQL in different environments and to use MySQL together with other database servers. 

​ For more information on setting the SQL mode, see [Section 5.1.11, “Server SQL Modes”](server-administration#sql-mode).

### Running MySQL in ANSI Mode



​ To run MySQL Server in ANSI mode, start [**mysqld**](programs#mysqld) with the [`--ansi`](server-administration#option_mysqld_ansi) option. Running the server in ANSI mode is the same as starting it with the following options: 

```
--transaction-isolation=SERIALIZABLE --sql-mode=ANSI
```

​ To achieve the same effect at runtime, execute these two statements: 

```
SET GLOBAL TRANSACTION ISOLATION LEVEL SERIALIZABLE;
SET GLOBAL sql_mode = 'ANSI';
```

​ You can see that setting the [`sql_mode`](server-administration#sysvar_sql_mode) system variable to `'ANSI'` enables all SQL mode options that are relevant for ANSI mode as follows: 

```
mysql> SET GLOBAL sql_mode='ANSI';
mysql> SELECT @@GLOBAL.sql_mode;
 -> 'REAL_AS_FLOAT,PIPES_AS_CONCAT,ANSI_QUOTES,IGNORE_SPACE,ANSI'
```

​ Running the server in ANSI mode with [`--ansi`](server-administration#option_mysqld_ansi) is not quite the same as setting the SQL mode to `'ANSI'` because the [`--ansi`](server-administration#option_mysqld_ansi) option also sets the transaction isolation level. 

​ See [Section 5.1.7, “Server Command Options”](server-administration#server-options).

### 1.8.1 MySQL Extensions to Standard SQL



​ MySQL Server supports some extensions that you probably will not find in other SQL DBMSs. Be warned that if you use them, your code will not be portable to other SQL servers. In some cases, you can write code that includes MySQL extensions, but is still portable, by using comments of the following form: 

```
/*! MySQL-specific code */
```

​ In this case, MySQL Server parses and executes the code within the comment as it would any other SQL statement, but other SQL servers will ignore the extensions. For example, MySQL Server recognizes the `STRAIGHT_JOIN` keyword in the following statement, but other servers will not: 

```
SELECT /*! STRAIGHT_JOIN */ col1 FROM table1,table2 WHERE ...
```

​ If you add a version number after the `!` character, the syntax within the comment is executed only if the MySQL version is greater than or equal to the specified version number. The `KEY_BLOCK_SIZE` clause in the following comment is executed only by servers from MySQL 5.1.10 or higher: 

```
CREATE TABLE t1(a INT, KEY (a)) /*!50110 KEY_BLOCK_SIZE=1024 */;
```

​ The following descriptions list MySQL extensions, organized by category.

-  Organization of data on disk 

 

 

 

 

 ​  MySQL Server maps each database to a directory under the  MySQL data directory, and maps tables within a database to  file names in the database directory. Consequently, database  and table names are case-sensitive in MySQL Server on  operating systems that have case-sensitive file names (such  as most Unix systems). See  [Section 9.2.3, “Identifier Case Sensitivity”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/language-structure.html#identifier-case-sensitivity). 

-  General language syntax

 - By default, strings can be enclosed by `"` as well as `'`. If the [`ANSI_QUOTES`](server-administration#sqlmode_ansi_quotes) SQL mode is enabled, strings can be enclosed only by `'` and the server interprets strings enclosed by `"` as identifiers. 
 - `\` is the escape character in strings. 
 - In SQL statements, you can access tables from different databases with the *`db_name.tbl_name`* syntax. Some SQL servers provide the same functionality but call this `User space`. MySQL Server doesn't support tablespaces such as used in statements like this: `CREATE TABLE ralph.my_table ... IN my_tablespace`.

-  SQL statement syntax

 - The [`ANALYZE TABLE`](sql-statements.html#analyze-table), [`CHECK TABLE`](sql-statements.html#check-table), [`OPTIMIZE TABLE`](sql-statements.html#optimize-table), and [`REPAIR TABLE`](sql-statements.html#repair-table) statements. 
 - The [`CREATE DATABASE`](sql-statements.html#create-database), [`DROP DATABASE`](sql-statements.html#drop-database), and [`ALTER DATABASE`](sql-statements.html#alter-database) statements. See [Section 13.1.12, “CREATE DATABASE Statement”](sql-statements.html#create-database), [Section 13.1.24, “DROP DATABASE Statement”](sql-statements.html#drop-database), and [Section 13.1.2, “ALTER DATABASE Statement”](sql-statements.html#alter-database). 
 - The [`DO`](sql-statements.html#do) statement. 
 - [`EXPLAIN SELECT`](sql-statements.html#explain) to obtain a description of how tables are processed by the query optimizer. 
 - The [`FLUSH`](sql-statements.html#flush) and [`RESET`](sql-statements.html#reset) statements. 
 - The [`SET`](sql-statements.html#set-variable) statement. See [Section 13.7.6.1, “SET Syntax for Variable Assignment”](sql-statements.html#set-variable). 
 - The [`SHOW`](sql-statements.html#show) statement. See [Section 13.7.7, “SHOW Statements”](sql-statements.html#show). The information produced by many of the MySQL-specific [`SHOW`](sql-statements.html#show) statements can be obtained in more standard fashion by using [`SELECT`](sql-statements.html#select) to query `INFORMATION_SCHEMA`. See [Chapter 25, *INFORMATION_SCHEMA Tables*](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html). 
 - Use of [`LOAD DATA`](sql-statements.html#load-data). In many cases, this syntax is compatible with Oracle [`LOAD DATA`](sql-statements.html#load-data). See [Section 13.2.7, “LOAD DATA Statement”](sql-statements.html#load-data). 
 - Use of [`RENAME TABLE`](sql-statements.html#rename-table). See [Section 13.1.36, “RENAME TABLE Statement”](sql-statements.html#rename-table). 
 - Use of [`REPLACE`](sql-statements.html#replace) instead of [`DELETE`](sql-statements.html#delete) plus [`INSERT`](sql-statements.html#insert). See [Section 13.2.9, “REPLACE Statement”](sql-statements.html#replace). 
 - Use of `CHANGE *`col_name`*`, `DROP *`col_name`*`, or [`DROP INDEX`](sql-statements.html#drop-index), `IGNORE` or `RENAME` in [`ALTER TABLE`](sql-statements.html#alter-table) statements. Use of multiple `ADD`, `ALTER`, `DROP`, or `CHANGE` clauses in an [`ALTER TABLE`](sql-statements.html#alter-table) statement. See [Section 13.1.9, “ALTER TABLE Statement”](sql-statements.html#alter-table). 
 - Use of index names, indexes on a prefix of a column, and use of `INDEX` or `KEY` in [`CREATE TABLE`](sql-statements.html#create-table) statements. See [Section 13.1.20, “CREATE TABLE Statement”](sql-statements.html#create-table). 
 - Use of `TEMPORARY` or `IF NOT EXISTS` with [`CREATE TABLE`](sql-statements.html#create-table). 
 - Use of `IF EXISTS` with [`DROP TABLE`](sql-statements.html#drop-table) and [`DROP DATABASE`](sql-statements.html#drop-database). 
 - The capability of dropping multiple tables with a single [`DROP TABLE`](sql-statements.html#drop-table) statement. 
 - The `ORDER BY` and `LIMIT` clauses of the [`UPDATE`](sql-statements.html#update) and [`DELETE`](sql-statements.html#delete) statements. 
 - `INSERT INTO *`tbl_name`* SET *`col_name`* = ...` syntax. 
 - The `DELAYED` clause of the [`INSERT`](sql-statements.html#insert) and [`REPLACE`](sql-statements.html#replace) statements. 
 - The `LOW_PRIORITY` clause of the [`INSERT`](sql-statements.html#insert), [`REPLACE`](sql-statements.html#replace), [`DELETE`](sql-statements.html#delete), and [`UPDATE`](sql-statements.html#update) statements. 
 - Use of `INTO OUTFILE` or `INTO DUMPFILE` in [`SELECT`](sql-statements.html#select) statements. See [Section 13.2.10, “SELECT Statement”](sql-statements.html#select). 
 - Options such as `STRAIGHT_JOIN` or `SQL_SMALL_RESULT` in [`SELECT`](sql-statements.html#select) statements. 
 - You don't need to name all selected columns in the `GROUP BY` clause. This gives better performance for some very specific, but quite normal queries. See [Section 12.20, “Aggregate Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#aggregate-functions-and-modifiers). 
 - You can specify `ASC` and `DESC` with `GROUP BY`, not just with `ORDER BY`. 
 - The ability to set variables in a statement with the `:=` assignment operator. See [Section 9.4, “User-Defined Variables”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/language-structure.html#user-variables).

-  Data types

 - The [`MEDIUMINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types), [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set), and [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum) data types, and the various [`BLOB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob) and [`TEXT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#blob) data types. 
 - The `AUTO_INCREMENT`, `BINARY`, `NULL`, `UNSIGNED`, and `ZEROFILL` data type attributes.

-  Functions and operators

 - To make it easier for users who migrate from other SQL environments, MySQL Server supports aliases for many functions. For example, all string functions support both standard SQL syntax and ODBC syntax. 

 - MySQL Server understands the [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) and [`&&`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and) operators to mean logical OR and AND, as in the C programming language. In MySQL Server, [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) and [`OR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) are synonyms, as are [`&&`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and) and [`AND`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and). Because of this nice syntax, MySQL Server doesn't support the standard SQL [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) operator for string concatenation; use [`CONCAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_concat) instead. Because [`CONCAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_concat) takes any number of arguments, it is easy to convert use of the [`||`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or) operator to MySQL Server. 

 - Use of [`COUNT(DISTINCT *`value_list`*)`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_count) where *`value_list`* has more than one element. 

 - String comparisons are case-insensitive by default, with sort ordering determined by the collation of the current character set, which is `utf8mb4` by default. To perform case-sensitive comparisons instead, you should declare your columns with the `BINARY` attribute or use the `BINARY` cast, which causes comparisons to be done using the underlying character code values rather than a lexical ordering. 

 - The [`%`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_mod) operator is a synonym for [`MOD()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_mod). That is, `*`N`* % *`M`*` is equivalent to [`MOD(*`N`*,*`M`*)`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_mod). [`%`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_mod) is supported for C programmers and for compatibility with PostgreSQL. 

 - The [`=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_equal), [`<>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not-equal), [`<=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_less-than-or-equal), [`<`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_less-than), [`>=`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_greater-than-or-equal), [`>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_greater-than), [`<<`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_left-shift), [`>>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_right-shift), [`<=>`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_equal-to), [`AND`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_and), [`OR`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_or), or [`LIKE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_like) operators may be used in expressions in the output column list (to the left of the `FROM`) in [`SELECT`](sql-statements.html#select) statements. For example: 

 ```
 mysql> SELECT col1=1 AND col2=2 FROM my_table;
 ```

 - The [`LAST_INSERT_ID()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_last-insert-id) function returns the most recent `AUTO_INCREMENT` value. See [Section 12.15, “Information Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#information-functions). 

 - [`LIKE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_like) is permitted on numeric values. 

 - The [`REGEXP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_regexp) and [`NOT REGEXP`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_not-regexp) extended regular expression operators. 

 - [`CONCAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_concat) or [`CHAR()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_char) with one argument or more than two arguments. (In MySQL Server, these functions can take a variable number of arguments.) 

 - The [`BIT_COUNT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_bit-count), [`CASE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#operator_case), [`ELT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_elt), [`FROM_DAYS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_from-days), [`FORMAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_format), [`IF()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_if), [`MD5()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_md5), [`PERIOD_ADD()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_period-add), [`PERIOD_DIFF()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_period-diff), [`TO_DAYS()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_to-days), and [`WEEKDAY()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_weekday) functions. 

 - Use of [`TRIM()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_trim) to trim substrings. Standard SQL supports removal of single characters only. 

 - The `GROUP BY` functions [`STD()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_std), [`BIT_OR()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_bit-or), [`BIT_AND()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_bit-and), [`BIT_XOR()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_bit-xor), and [`GROUP_CONCAT()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_group-concat). See [Section 12.20, “Aggregate Functions”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#aggregate-functions-and-modifiers).

### 1.8.2 MySQL Differences from Standard SQL

- [1.8.2.1 SELECT INTO TABLE Differences](#ansi-diff-select-into-table)
- [1.8.2.2 UPDATE Differences](#ansi-diff-update)
- [1.8.2.3 FOREIGN KEY Constraint Differences](#ansi-diff-foreign-keys)
- [1.8.2.4 '--' as the Start of a Comment](#ansi-diff-comments)



​ We try to make MySQL Server follow the ANSI SQL standard and the ODBC SQL standard, but MySQL Server performs operations differently in some cases:

-  There are several differences between the MySQL and standard  SQL privilege systems. For example, in MySQL, privileges for  a table are not automatically revoked when you delete a  table. You must explicitly issue a  [`REVOKE`](sql-statements.html#revoke) statement to revoke  privileges for a table. For more information, see  [Section 13.7.1.8, “REVOKE Statement”](sql-statements.html#revoke). 
-  The [`CAST()`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#function_cast) function does not  support cast to [`REAL`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#floating-point-types) or  [`BIGINT`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#integer-types). See  [Section 12.10, “Cast Functions and Operators”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/functions.html#cast-functions).

#### 1.8.2.1 SELECT INTO TABLE Differences



​ MySQL Server doesn't support the `SELECT ... INTO TABLE` Sybase SQL extension. Instead, MySQL Server supports the [`INSERT INTO ... SELECT`](sql-statements.html#insert-select) standard SQL syntax, which is basically the same thing. See [Section 13.2.6.1, “INSERT ... SELECT Statement”](sql-statements.html#insert-select). For example: 

```
INSERT INTO tbl_temp2 (fld_id)
 SELECT tbl_temp1.fld_order_id
 FROM tbl_temp1 WHERE tbl_temp1.fld_order_id > 100;
```

​ Alternatively, you can use [`SELECT ... INTO OUTFILE`](sql-statements.html#select-into) or [`CREATE TABLE ... SELECT`](sql-statements.html#create-table). 

​ You can use [`SELECT ... INTO`](sql-statements.html#select) with user-defined variables. The same syntax can also be used inside stored routines using cursors and local variables. See [Section 13.2.10.1, “SELECT ... INTO Statement”](sql-statements.html#select-into).

#### 1.8.2.2 UPDATE Differences



​ If you access a column from the table to be updated in an expression, [`UPDATE`](sql-statements.html#update) uses the current value of the column. The second assignment in the following statement sets `col2` to the current (updated) `col1` value, not the original `col1` value. The result is that `col1` and `col2` have the same value. This behavior differs from standard SQL. 

```
UPDATE t1 SET col1 = col1 + 1, col2 = col1;
```

#### 1.8.2.3 FOREIGN KEY Constraint Differences



​ The MySQL implementation of foreign key constraints differs from the SQL standard in the following key respects:

- If there are several rows in the parent table with the same referenced key value, [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) performs a foreign key check as if the other parent rows with the same key value do not exist. For example, if you define a `RESTRICT` type constraint, and there is a child row with several parent rows, `InnoDB` does not permit the deletion of any of the parent rows.  

- If `ON UPDATE CASCADE` or `ON UPDATE SET NULL` recurses to update the *same table* it has previously updated during the same cascade, it acts like `RESTRICT`. This means that you cannot use self-referential `ON UPDATE CASCADE` or `ON UPDATE SET NULL` operations. This is to prevent infinite loops resulting from cascaded updates. A self-referential `ON DELETE SET NULL`, on the other hand, is possible, as is a self-referential `ON DELETE CASCADE`. Cascading operations may not be nested more than 15 levels deep.  

- In an SQL statement that inserts, deletes, or updates many rows, foreign key constraints (like unique constraints) are checked row-by-row. When performing foreign key checks, [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) sets shared row-level locks on child or parent records that it must examine. MySQL checks foreign key constraints immediately; the check is not deferred to transaction commit. According to the SQL standard, the default behavior should be deferred checking. That is, constraints are only checked after the *entire SQL statement* has been processed. This means that it is not possible to delete a row that refers to itself using a foreign key.  

- No storage engine, including `InnoDB`, recognizes or enforces the `MATCH` clause used in referential-integrity constraint definitions. Use of an explicit `MATCH` clause does not have the specified effect, and it causes `ON DELETE` and `ON UPDATE` clauses to be ignored. Specifying the `MATCH` should be avoided.  

 ​ The `MATCH` clause in the SQL standard controls how `NULL` values in a composite (multiple-column) foreign key are handled when comparing to a primary key in the referenced table. MySQL essentially implements the semantics defined by `MATCH SIMPLE`, which permits a foreign key to be all or partially `NULL`. In that case, a (child table) row containing such a foreign key can be inserted even though it does not match any row in the referenced (parent) table. (It is possible to implement other semantics using triggers.)  

- MySQL requires that the referenced columns be indexed for performance reasons. However, MySQL does not enforce a requirement that the referenced columns be `UNIQUE` or be declared `NOT NULL`.  

 ​ A `FOREIGN KEY` constraint that references a non-`UNIQUE` key is not standard SQL but rather an [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html) extension. The [`NDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/mysql-cluster.html) storage engine, on the other hand, requires an explicit unique key (or primary key) on any column referenced as a foreign key.  

 ​ The handling of foreign key references to nonunique keys or keys that contain `NULL` values is not well defined for operations such as [`UPDATE`](sql-statements.html#update) or `DELETE CASCADE`. You are advised to use foreign keys that reference only `UNIQUE` (including `PRIMARY`) and `NOT NULL` keys.  

- MySQL parses but ignores “inline `REFERENCES` specifications” (as defined in the SQL standard) where the references are defined as part of the column specification. MySQL accepts `REFERENCES` clauses only when specified as part of a separate `FOREIGN KEY` specification. For storage engines that do not support foreign keys (such as [`MyISAM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/storage-engines.html#myisam-storage-engine)), MySQL Server parses and ignores foreign key specifications.

​ For information about foreign key constraints, see [Section 13.1.20.5, “FOREIGN KEY Constraints”](sql-statements.html#create-table-foreign-keys).

#### 1.8.2.4 '--' as the Start of a Comment



​ Standard SQL uses the C syntax `/* this is a comment */` for comments, and MySQL Server supports this syntax as well. MySQL also support extensions to this syntax that enable MySQL-specific SQL to be embedded in the comment, as described in [Section 9.6, “Comment Syntax”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/language-structure.html#comments). 

​ Standard SQL uses “`--`” as a start-comment sequence. MySQL Server uses `#` as the start comment character. MySQL Server also supports a variant of the `--` comment style. That is, the `--` start-comment sequence must be followed by a space (or by a control character such as a newline). The space is required to prevent problems with automatically generated SQL queries that use constructs such as the following, where we automatically insert the value of the payment for `payment`: 

```
UPDATE account SET credit=credit-payment
```

​ Consider about what happens if `payment` has a negative value such as `-1`: 

```
UPDATE account SET credit=credit--1
```

​ `credit--1` is a valid expression in SQL, but `--` is interpreted as the start of a comment, part of the expression is discarded. The result is a statement that has a completely different meaning than intended: 

```
UPDATE account SET credit=credit
```

​ The statement produces no change in value at all. This illustrates that permitting comments to start with `--` can have serious consequences. 

​ Using our implementation requires a space following the `--` for it to be recognized as a start-comment sequence in MySQL Server. Therefore, `credit--1` is safe to use. 

​ Another safe feature is that the [**mysql**](programs#mysql) command-line client ignores lines that start with `--`.

### 1.8.3 How MySQL Deals with Constraints

- [1.8.3.1 PRIMARY KEY and UNIQUE Index Constraints](#constraint-primary-key)
- [1.8.3.2 FOREIGN KEY Constraints](#constraint-foreign-key)
- [1.8.3.3 Enforced Constraints on Invalid Data](#constraint-invalid-data)
- [1.8.3.4 ENUM and SET Constraints](#constraint-enum)



​ MySQL enables you to work both with transactional tables that permit rollback and with nontransactional tables that do not. Because of this, constraint handling is a bit different in MySQL than in other DBMSs. We must handle the case when you have inserted or updated a lot of rows in a nontransactional table for which changes cannot be rolled back when an error occurs. 

​ The basic philosophy is that MySQL Server tries to produce an error for anything that it can detect while parsing a statement to be executed, and tries to recover from any errors that occur while executing the statement. We do this in most cases, but not yet for all. 

​ The options MySQL has when an error occurs are to stop the statement in the middle or to recover as well as possible from the problem and continue. By default, the server follows the latter course. This means, for example, that the server may coerce invalid values to the closest valid values. 

​ Several SQL mode options are available to provide greater control over handling of bad data values and whether to continue statement execution or abort when errors occur. Using these options, you can configure MySQL Server to act in a more traditional fashion that is like other DBMSs that reject improper input. The SQL mode can be set globally at server startup to affect all clients. Individual clients can set the SQL mode at runtime, which enables each client to select the behavior most appropriate for its requirements. See [Section 5.1.11, “Server SQL Modes”](server-administration#sql-mode). 

​ The following sections describe how MySQL Server handles different types of constraints.

#### 1.8.3.1 PRIMARY KEY and UNIQUE Index Constraints



​ Normally, errors occur for data-change statements (such as [`INSERT`](sql-statements.html#insert) or [`UPDATE`](sql-statements.html#update)) that would violate primary-key, unique-key, or foreign-key constraints. If you are using a transactional storage engine such as `InnoDB`, MySQL automatically rolls back the statement. If you are using a nontransactional storage engine, MySQL stops processing the statement at the row for which the error occurred and leaves any remaining rows unprocessed. 

​ MySQL supports an `IGNORE` keyword for [`INSERT`](sql-statements.html#insert), [`UPDATE`](sql-statements.html#update), and so forth. If you use it, MySQL ignores primary-key or unique-key violations and continues processing with the next row. See the section for the statement that you are using ([Section 13.2.6, “INSERT Statement”](sql-statements.html#insert), [Section 13.2.13, “UPDATE Statement”](sql-statements.html#update), and so forth). 

​ You can get information about the number of rows actually inserted or updated with the [`mysql_info()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-info.html) C API function. You can also use the [`SHOW WARNINGS`](sql-statements.html#show-warnings) statement. See [mysql_info()](https://dev.mysql.com/doc/c-api/8.0/en/mysql-info.html), and [Section 13.7.7.40, “SHOW WARNINGS Statement”](sql-statements.html#show-warnings). 

​ `InnoDB` and `NDB` tables support foreign keys. See [Section 1.8.3.2, “FOREIGN KEY Constraints”](#constraint-foreign-key).

#### 1.8.3.2 FOREIGN KEY Constraints



​ Foreign keys let you cross-reference related data across tables, and [foreign key constraints](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/glossary.html#glos_foreign_key_constraint) help keep this spread-out data consistent. 

​ MySQL supports `ON UPDATE` and `ON DELETE` foreign key references in [`CREATE TABLE`](sql-statements.html#create-table) and [`ALTER TABLE`](sql-statements.html#alter-table) statements. The available referential actions are `RESTRICT`, `CASCADE`, `SET NULL`, and `NO ACTION` (the default). 

​ `SET DEFAULT` is also supported by the MySQL Server but is currently rejected as invalid by [`InnoDB`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/innodb-storage-engine.html). Since MySQL does not support deferred constraint checking, `NO ACTION` is treated as `RESTRICT`. For the exact syntax supported by MySQL for foreign keys, see [Section 13.1.20.5, “FOREIGN KEY Constraints”](sql-statements.html#create-table-foreign-keys). 

​ `MATCH FULL`, `MATCH PARTIAL`, and `MATCH SIMPLE` are allowed, but their use should be avoided, as they cause the MySQL Server to ignore any `ON DELETE` or `ON UPDATE` clause used in the same statement. `MATCH` options do not have any other effect in MySQL, which in effect enforces `MATCH SIMPLE` semantics full-time. 

​ MySQL requires that foreign key columns be indexed; if you create a table with a foreign key constraint but no index on a given column, an index is created. 

​ You can obtain information about foreign keys from the [`INFORMATION_SCHEMA.KEY_COLUMN_USAGE`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-key-column-usage-table) table. An example of a query against this table is shown here: 

```
mysql> SELECT TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, CONSTRAINT_NAME
  > FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE
  > WHERE REFERENCED_TABLE_SCHEMA IS NOT NULL;
+--------------+---------------+-------------+-----------------+
| TABLE_SCHEMA | TABLE_NAME | COLUMN_NAME | CONSTRAINT_NAME |
+--------------+---------------+-------------+-----------------+
| fk1 | myuser | myuser_id | f |
| fk1 | product_order | customer_id | f2 |
| fk1 | product_order | product_id | f1 |
+--------------+---------------+-------------+-----------------+
3 rows in set (0.01 sec)
```

​ Information about foreign keys on `InnoDB` tables can also be found in the [`INNODB_FOREIGN`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-foreign-table) and [`INNODB_FOREIGN_COLS`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/information-schema.html#information-schema-innodb-foreign-cols-table) tables, in the `INFORMATION_SCHEMA` database. 

​ `InnoDB` and `NDB` tables support foreign keys.

#### 1.8.3.3 Enforced Constraints on Invalid Data



​ By default, MySQL 8.0 rejects invalid or improper data values and aborts the statement in which they occur. It is possible to alter this behavior to be more forgiving of invalid values, such that the server coerces them to valid ones for data entry, by disabling strict SQL mode (see [Section 5.1.11, “Server SQL Modes”](server-administration#sql-mode)), but this is not recommended. 

​ Older versions of MySQL employed the forgiving behavior by default; for a description of this behavior, see [Constraints on Invalid Data](https://dev.mysql.com/doc/refman/5.7/en/constraint-invalid-data.html).

#### 1.8.3.4 ENUM and SET Constraints

​ [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum) and [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set) columns provide an efficient way to define columns that can contain only a given set of values. See [Section 11.3.5, “The ENUM Type”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum), and [Section 11.3.6, “The SET Type”](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set). 

​ Unless strict mode is disabled (not recommended, but see [Section 5.1.11, “Server SQL Modes”](server-administration#sql-mode)), the definition of a [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum) or [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set) column acts as a constraint on values entered into the column. An error occurs for values that do not satisfy these conditions:

- An [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum) value must be one of those listed in the column definition, or the internal numeric equivalent thereof. The value cannot be the error value (that is, 0 or the empty string). For a column defined as [`ENUM('a','b','c')`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum), values such as `''`, `'d'`, or `'ax'` are invalid and are rejected.  
- A [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set) value must be the empty string or a value consisting only of the values listed in the column definition separated by commas. For a column defined as [`SET('a','b','c')`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set), values such as `'d'` or `'a,b,c,d'` are invalid and are rejected.

​ Errors for invalid values can be suppressed in strict mode if you use [`INSERT IGNORE`](sql-statements.html#insert) or `UPDATE IGNORE`. In this case, a warning is generated rather than an error. For [`ENUM`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#enum), the value is inserted as the error member (`0`). For [`SET`](file:///C:/Users/ADMINI~1/AppData/Local/Temp/Rar$EXa8608.40669/refman-8.0-en.html-chapter/data-types.html#set), the value is inserted as given except that any invalid substrings are deleted. For example, `'a,x,b,y'` results in a value of `'a,b'`.

## 1.9 Credits

- [1.9.1 Contributors to MySQL](#contributors)
- [1.9.2 Documenters and translators](#documenters-translators)
- [1.9.3 Packages that support MySQL](#packages)
- [1.9.4 Tools that were used to create MySQL](#tools-used-to-create-mysql)
- [1.9.5 Supporters of MySQL](#supporters)

​ The following sections list developers, contributors, and supporters that have helped to make MySQL what it is today.

### 1.9.1 Contributors to MySQL



​ Although Oracle Corporation and/or its affiliates own all copyrights in the `MySQL server` and the `MySQL manual`, we wish to recognize those who have made contributions of one kind or another to the `MySQL distribution`. Contributors are listed here, in somewhat random order:

- Gianmassimo Vigazzola `<qwerg@mbox.vol.it>` or `<qwerg@tin.it>` 

 ​ The initial port to Win32/NT. 

- Per Eric Olsson 

 ​ For constructive criticism and real testing of the dynamic record format. 

- Irena Pancirov `<irena@mail.yacc.it>` 

 ​ Win32 port with Borland compiler. `mysqlshutdown.exe` and `mysqlwatch.exe`. 

- David J. Hughes 

 ​ For the effort to make a shareware SQL database. At TcX, the predecessor of MySQL AB, we started with `mSQL`, but found that it couldn't satisfy our purposes so instead we wrote an SQL interface to our application builder Unireg. [**mysqladmin**](programs#mysqladmin) and [**mysql**](programs#mysql) client are programs that were largely influenced by their `mSQL` counterparts. We have put a lot of effort into making the MySQL syntax a superset of `mSQL`. Many of the API's ideas are borrowed from `mSQL` to make it easy to port free `mSQL` programs to the MySQL API. The MySQL software doesn't contain any code from `mSQL`. Two files in the distribution (`client/insert_test.c` and `client/select_test.c`) are based on the corresponding (noncopyrighted) files in the `mSQL` distribution, but are modified as examples showing the changes necessary to convert code from `mSQL` to MySQL Server. (`mSQL` is copyrighted David J. Hughes.) 

- Patrick Lynch 

 ​ For helping us acquire http://www.mysql.com/. 

- Fred Lindberg 

 ​ For setting up qmail to handle the MySQL mailing list and for the incredible help we got in managing the MySQL mailing lists. 

- Igor Romanenko `<igor@frog.kiev.ua>` 

 ​ [**mysqldump**](programs#mysqldump) (previously `msqldump`, but ported and enhanced by Monty). 

- Yuri Dario 

 ​ For keeping up and extending the MySQL OS/2 port. 

- Tim Bunce 

 ​ Author of **mysqlhotcopy**. 

- Zarko Mocnik `<zarko.mocnik@dem.si>` 

 ​ Sorting for Slovenian language. 

- "TAMITO" `<tommy@valley.ne.jp>` 

 ​ The `_MB` character set macros and the ujis and sjis character sets. 

- Joshua Chamas `<joshua@chamas.com>` 

 ​ Base for concurrent insert, extended date syntax, debugging on NT, and answering on the MySQL mailing list. 

- Yves Carlier `<Yves.Carlier@rug.ac.be>` 

 ​ **mysqlaccess**, a program to show the access rights for a user. 

- Rhys Jones `<rhys@wales.com>` (And GWE Technologies Limited) 

 ​ For one of the early JDBC drivers. 

- Dr Xiaokun Kelvin ZHU `<X.Zhu@brad.ac.uk>` 

 ​ Further development of one of the early JDBC drivers and other MySQL-related Java tools. 

- James Cooper `<pixel@organic.com>` 

 ​ For setting up a searchable mailing list archive at his site. 

- Rick Mehalick `<Rick_Mehalick@i-o.com>` 

 ​ For `xmysql`, a graphical X client for MySQL Server. 

- Doug Sisk `<sisk@wix.com>` 

 ​ For providing RPM packages of MySQL for Red Hat Linux. 

- Diemand Alexander V. `<axeld@vial.ethz.ch>` 

 ​ For providing RPM packages of MySQL for Red Hat Linux-Alpha. 

- Antoni Pamies Olive `<toni@readysoft.es>` 

 ​ For providing RPM versions of a lot of MySQL clients for Intel and SPARC. 

- Jay Bloodworth `<jay@pathways.sde.state.sc.us>` 

 ​ For providing RPM versions for MySQL 3.21. 

- David Sacerdote `<davids@secnet.com>` 

 ​ Ideas for secure checking of DNS host names. 

- Wei-Jou Chen `<jou@nematic.ieo.nctu.edu.tw>` 

 ​ Some support for Chinese(BIG5) characters. 

- Wei He `<hewei@mail.ied.ac.cn>` 

 ​ A lot of functionality for the Chinese(GBK) character set. 

- Jan Pazdziora `<adelton@fi.muni.cz>` 

 ​ Czech sorting order. 

- Zeev Suraski `<bourbon@netvision.net.il>` 

 ​ `FROM_UNIXTIME()` time formatting, `ENCRYPT()` functions, and **bison** advisor. Active mailing list member. 

- Luuk de Boer `<luuk@wxs.nl>` 

 ​ Ported (and extended) the benchmark suite to `DBI`/`DBD`. Have been of great help with `crash-me` and running benchmarks. Some new date functions. The **mysql_setpermission** script. 

- Alexis Mikhailov `<root@medinf.chuvashia.su>` 

 ​ User-defined functions (UDFs); [`CREATE FUNCTION`](sql-statements.html#create-function) and [`DROP FUNCTION`](sql-statements.html#drop-function). 

- Andreas F. Bobak `<bobak@relog.ch>` 

 ​ The `AGGREGATE` extension to user-defined functions. 

- Ross Wakelin `<R.Wakelin@march.co.uk>` 

 ​ Help to set up InstallShield for MySQL-Win32. 

- Jethro Wright III `<jetman@li.net>` 

 ​ The `libmysql.dll` library. 

- James Pereria `<jpereira@iafrica.com>` 

 ​ Mysqlmanager, a Win32 GUI tool for administering MySQL Servers. 

- Curt Sampson `<cjs@portal.ca>` 

 ​ Porting of MIT-pthreads to NetBSD/Alpha and NetBSD 1.3/i386. 

- Martin Ramsch `<m.ramsch@computer.org>` 

 ​ Examples in the MySQL Tutorial. 

- Steve Harvey 

 ​ For making **mysqlaccess** more secure. 

- Konark IA-64 Centre of Persistent Systems Private Limited 

 ​ Help with the Win64 port of the MySQL server. 

- Albert Chin-A-Young. 

 ​ Configure updates for Tru64, large file support and better TCP wrappers support. 

- John Birrell 

 ​ Emulation of `pthread_mutex()` for OS/2. 

- Benjamin Pflugmann 

 ​ Extended `MERGE` tables to handle `INSERTS`. Active member on the MySQL mailing lists. 

- Jocelyn Fournier 

 ​ Excellent spotting and reporting innumerable bugs (especially in the MySQL 4.1 subquery code). 

- Marc Liyanage 

 ​ Maintaining the OS X packages and providing invaluable feedback on how to create OS X packages. 

- Robert Rutherford 

 ​ Providing invaluable information and feedback about the QNX port. 

- Previous developers of NDB Cluster 

 ​ Lots of people were involved in various ways summer students, master thesis students, employees. In total more than 100 people so too many to mention here. Notable name is Ataullah Dabaghi who up until 1999 contributed around a third of the code base. A special thanks also to developers of the AXE system which provided much of the architectural foundations for NDB Cluster with blocks, signals and crash tracing functionality. Also credit should be given to those who believed in the ideas enough to allocate of their budgets for its development from 1992 to present time. 

- Google Inc. 

 ​ We wish to recognize Google Inc. for contributions to the MySQL distribution: Mark Callaghan's SMP Performance patches and other patches.

​ Other contributors, bugfinders, and testers: James H. Thompson, Maurizio Menghini, Wojciech Tryc, Luca Berra, Zarko Mocnik, Wim Bonis, Elmar Haneke, `<jehamby@lightside>`, `<psmith@BayNetworks.com>`, `<duane@connect.com.au>`, Ted Deppner `<ted@psyber.com>`, Mike Simons, Jaakko Hyvatti. 

​ And lots of bug report/patches from the folks on the mailing list. 

​ A big tribute goes to those that help us answer questions on the MySQL mailing lists:

- Daniel Koch `<dkoch@amcity.com>` 

 ​ Irix setup. 

- Luuk de Boer `<luuk@wxs.nl>` 

 ​ Benchmark questions. 

- Tim Sailer `<tps@users.buoy.com>` 

 ​ `DBD::mysql` questions. 

- Boyd Lynn Gerber `<gerberb@zenez.com>` 

 ​ SCO-related questions. 

- Richard Mehalick `<RM186061@shellus.com>` 

 ​ `xmysql`-related questions and basic installation questions. 

- Zeev Suraski `<bourbon@netvision.net.il>` 

 ​ Apache module configuration questions (log & auth), PHP-related questions, SQL syntax-related questions and other general questions. 

- Francesc Guasch `<frankie@citel.upc.es>` 

 ​ General questions. 

- Jonathan J Smith `<jsmith@wtp.net>` 

 ​ Questions pertaining to OS-specifics with Linux, SQL syntax, and other things that might need some work. 

- David Sklar `<sklar@student.net>` 

 ​ Using MySQL from PHP and Perl. 

- Alistair MacDonald `<A.MacDonald@uel.ac.uk>` 

 ​ Is flexible and can handle Linux and perhaps HP-UX. 

- John Lyon `<jlyon@imag.net>` 

 ​ Questions about installing MySQL on Linux systems, using either `.rpm` files or compiling from source. 

- Lorvid Ltd. `<lorvid@WOLFENET.com>` 

 ​ Simple billing/license/support/copyright issues. 

- Patrick Sherrill `<patrick@coconet.com>` 

 ​ ODBC and VisualC++ interface questions. 

- Randy Harmon `<rjharmon@uptimecomputers.com>` 

 ​ `DBD`, Linux, some SQL syntax questions.

### 1.9.2 Documenters and translators



​ The following people have helped us with writing the MySQL documentation and translating the documentation or error messages in MySQL.

- Paul DuBois 

 ​ Ongoing help with making this manual correct and understandable. That includes rewriting Monty's and David's attempts at English into English as other people know it. 

- Kim Aldale 

 ​ Helped to rewrite Monty's and David's early attempts at English into English. 

- Michael J. Miller Jr. `<mke@terrapin.turbolift.com>` 

 ​ For the first MySQL manual. And a lot of spelling/language fixes for the FAQ (that turned into the MySQL manual a long time ago). 

- Yan Cailin 

 ​ First translator of the MySQL Reference Manual into simplified Chinese in early 2000 on which the Big5 and HK coded versions were based. 

- Jay Flaherty `<fty@mediapulse.com>` 

 ​ Big parts of the Perl `DBI`/`DBD` section in the manual. 

- Paul Southworth `<pauls@etext.org>`, Ray Loyzaga `<yar@cs.su.oz.au>` 

 ​ Proof-reading of the Reference Manual. 

- Therrien Gilbert `<gilbert@ican.net>`, Jean-Marc Pouyot `<jmp@scalaire.fr>` 

 ​ French error messages. 

- Petr Snajdr, `<snajdr@pvt.net>` 

 ​ Czech error messages. 

- Jaroslaw Lewandowski `<jotel@itnet.com.pl>` 

 ​ Polish error messages. 

- Miguel Angel Fernandez Roiz 

 ​ Spanish error messages. 

- Roy-Magne Mo `<rmo@www.hivolda.no>` 

 ​ Norwegian error messages and testing of MySQL 3.21.xx. 

- Timur I. Bakeyev `<root@timur.tatarstan.ru>` 

 ​ Russian error messages. 

- `<brenno@dewinter.com>` & Filippo Grassilli `<phil@hyppo.com>` 

 ​ Italian error messages. 

- Dirk Munzinger `<dirk@trinity.saar.de>` 

 ​ German error messages. 

- Billik Stefan `<billik@sun.uniag.sk>` 

 ​ Slovak error messages. 

- Stefan Saroiu `<tzoompy@cs.washington.edu>` 

 ​ Romanian error messages. 

- Peter Feher 

 ​ Hungarian error messages. 

- Roberto M. Serqueira 

 ​ Portuguese error messages. 

- Carsten H. Pedersen 

 ​ Danish error messages. 

- Arjen Lentz 

 ​ Dutch error messages, completing earlier partial translation (also work on consistency and spelling).

### 1.9.3 Packages that support MySQL



​ The following is a list of creators/maintainers of some of the most important API/packages/applications that a lot of people use with MySQL. 

​ We cannot list every possible package here because the list would then be way to hard to maintain. For other packages, please refer to the software portal at http://solutions.mysql.com/software/.

- Tim Bunce, Alligator Descartes 

 ​ For the `DBD` (Perl) interface. 

- Andreas Koenig `<a.koenig@mind.de>` 

 ​ For the Perl interface for MySQL Server. 

- Jochen Wiedmann `<wiedmann@neckar-alb.de>` 

 ​ For maintaining the Perl `DBD::mysql` module. 

- Eugene Chan `<eugene@acenet.com.sg>` 

 ​ For porting PHP for MySQL Server. 

- Georg Richter 

 ​ MySQL 4.1 testing and bug hunting. New PHP 5.0 `mysqli` extension (API) for use with MySQL 4.1 and up. 

- Giovanni Maruzzelli `<maruzz@matrice.it>` 

 ​ For porting iODBC (Unix ODBC). 

- Xavier Leroy `<Xavier.Leroy@inria.fr>` 

 ​ The author of LinuxThreads (used by the MySQL Server on Linux).

### 1.9.4 Tools that were used to create MySQL



​ The following is a list of some of the tools we have used to create MySQL. We use this to express our thanks to those that has created them as without these we could not have made MySQL what it is today.

- Free Software Foundation 

 ​ From whom we got an excellent compiler (**gcc**), an excellent debugger (**gdb** and the `libc` library (from which we have borrowed `strto.c` to get some code working in Linux). 

- Free Software Foundation & The XEmacs development team 

 ​ For a really great editor/environment. 

- Julian Seward 

 ​ Author of `valgrind`, an excellent memory checker tool that has helped us find a lot of otherwise hard to find bugs in MySQL. 

- Dorothea Lütkehaus and Andreas Zeller 

 ​ For `DDD` (The Data Display Debugger) which is an excellent graphical front end to **gdb**).

### 1.9.5 Supporters of MySQL



​ Although Oracle Corporation and/or its affiliates own all copyrights in the `MySQL server` and the `MySQL manual`, we wish to recognize the following companies, which helped us finance the development of the `MySQL server`, such as by paying us for developing a new feature or giving us hardware for development of the `MySQL server`.

- VA Linux / Andover.net 

 ​ Funded replication. 

- NuSphere 

 ​ Editing of the MySQL manual. 

- Stork Design studio 

 ​ The MySQL website in use between 1998-2000. 

- Intel 

 ​ Contributed to development on Windows and Linux platforms. 

- Compaq 

 ​ Contributed to Development on Linux/Alpha. 

- SWSoft 

 ​ Development on the embedded [**mysqld**](programs#mysqld) version. 

- FutureQuest 

 ​ The `--skip-show-database` option.