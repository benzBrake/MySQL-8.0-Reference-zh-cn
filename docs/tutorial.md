# 第三章 使用教程

​    This chapter provides a tutorial introduction to MySQL by showing    how to use the [**mysql**](programs.md#mysql) client program to create and    use a simple database. [**mysql**](programs.md#mysql) (sometimes referred    to as the “terminal monitor” or just    “monitor”) is an interactive program that enables you    to connect to a MySQL server, run queries, and view the results.    [**mysql**](programs.md#mysql) may also be used in batch mode: you place    your queries in a file beforehand, then tell    [**mysql**](programs.md#mysql) to execute the contents of the file. Both    ways of using [**mysql**](programs.md#mysql) are covered here.  

​    To see a list of options provided by [**mysql**](programs.md#mysql),    invoke it with the [`--help`](programs.md#option_mysql_help) option:  

```
shell> mysql --help
```

​    This chapter assumes that [**mysql**](programs.md#mysql) is installed on    your machine and that a MySQL server is available to which you can    connect. If this is not true, contact your MySQL administrator. (If    *you* are the administrator, you need to consult    the relevant portions of this manual, such as    [Chapter 5, *MySQL Server Administration*](server-administration.md).)  

​    This chapter describes the entire process of setting up and using a    database. If you are interested only in accessing an existing    database, you may want to skip the sections that describe how to    create the database and the tables it contains.  

​    Because this chapter is tutorial in nature, many details are    necessarily omitted. Consult the relevant sections of the manual for    more information on the topics covered here.

## 3.1 Connecting to and Disconnecting from the Server



​      To connect to the server, you will usually need to provide a MySQL      user name when you invoke [**mysql**](programs.md#mysql) and, most      likely, a password. If the server runs on a machine other than the      one where you log in, you will also need to specify a host name.      Contact your administrator to find out what connection parameters      you should use to connect (that is, what host, user name, and      password to use). Once you know the proper parameters, you should      be able to connect like this:    

```
shell> mysql -h host -u user -p
Enter password: ********
```

​      *`host`* and      *`user`* represent the host name where your      MySQL server is running and the user name of your MySQL account.      Substitute appropriate values for your setup. The      `********` represents your password; enter it      when [**mysql**](programs.md#mysql) displays the `Enter      password:` prompt.    

​      If that works, you should see some introductory information      followed by a `mysql>` prompt:    

```
shell> mysql -h host -u user -p
Enter password: ********
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 25338 to server version: 8.0.23-standard

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

​      The `mysql>` prompt tells you that      [**mysql**](programs.md#mysql) is ready for you to enter SQL statements.    

​      If you are logging in on the same machine that MySQL is running      on, you can omit the host, and simply use the following:    

```
shell> mysql -u user -p
```

​      If, when you attempt to log in, you get an error message such as      ERROR 2002 (HY000): Can't connect to local MySQL server      through socket '/tmp/mysql.sock' (2), it means that      the MySQL server daemon (Unix) or service (Windows) is not      running. Consult the administrator or see the section of      [Chapter 2, *Installing and Upgrading MySQL*](installing.md) that is appropriate to your operating      system.    

​      For help with other problems often encountered when trying to log      in, see [Section B.3.2, “Common Errors When Using MySQL Programs”](error-handling.md#common-errors).    

​      Some MySQL installations permit users to connect as the anonymous      (unnamed) user to the server running on the local host. If this is      the case on your machine, you should be able to connect to that      server by invoking [**mysql**](programs.md#mysql) without any options:    

```
shell> mysql
```

​      After you have connected successfully, you can disconnect any time      by typing `QUIT` (or `\q`) at      the `mysql>` prompt:    

```
mysql> QUIT
Bye
```

​      On Unix, you can also disconnect by pressing Control+D.    

​      Most examples in the following sections assume that you are      connected to the server. They indicate this by the      `mysql>` prompt.

## 3.2 Entering Queries



​      Make sure that you are connected to the server, as discussed in      the previous section. Doing so does not in itself select any      database to work with, but that is okay. At this point, it is more      important to find out a little about how to issue queries than to      jump right in creating tables, loading data into them, and      retrieving data from them. This section describes the basic      principles of entering queries, using several queries you can try      out to familiarize yourself with how [**mysql**](programs.md#mysql)      works.    

​      Here is a simple query that asks the server to tell you its      version number and the current date. Type it in as shown here      following the `mysql>` prompt and press Enter:    

```
mysql> SELECT VERSION(), CURRENT_DATE;
+-----------+--------------+
| VERSION() | CURRENT_DATE |
+-----------+--------------+
| 5.8.0-m17 | 2015-12-21   |
+-----------+--------------+
1 row in set (0.02 sec)
mysql>
```

​      This query illustrates several things about      [**mysql**](programs.md#mysql):

- ​ A query normally consists of an SQL statement followed by a semicolon. (There are some exceptions where a semicolon may be omitted. `QUIT`, mentioned earlier, is one of them. We'll get to others later.)        
- ​ When you issue a query, [**mysql**](programs.md#mysql) sends it to the server for execution and displays the results, then prints another `mysql>` prompt to indicate that it is ready for another query.        
- ​ [**mysql**](programs.md#mysql) displays query output in tabular form (rows and columns). The first row contains labels for the columns. The rows following are the query results. Normally, column labels are the names of the columns you fetch from database tables. If you're retrieving the value of an expression rather than a table column (as in the example just shown), [**mysql**](programs.md#mysql) labels the column using the expression itself.        
- ​ [**mysql**](programs.md#mysql) shows how many rows were returned and how long the query took to execute, which gives you a rough idea of server performance. These values are imprecise because they represent wall clock time (not CPU or machine time), and because they are affected by factors such as server load and network latency. (For brevity, the “rows in set” line is sometimes not shown in the remaining examples in this chapter.)

​      Keywords may be entered in any lettercase. The following queries      are equivalent:    

```
mysql> SELECT VERSION(), CURRENT_DATE;
mysql> select version(), current_date;
mysql> SeLeCt vErSiOn(), current_DATE;
```

​      Here is another query. It demonstrates that you can use      [**mysql**](programs.md#mysql) as a simple calculator:    

```
mysql> SELECT SIN(PI()/4), (4+1)*5;
+------------------+---------+
| SIN(PI()/4)      | (4+1)*5 |
+------------------+---------+
| 0.70710678118655 |      25 |
+------------------+---------+
1 row in set (0.02 sec)
```

​      The queries shown thus far have been relatively short, single-line      statements. You can even enter multiple statements on a single      line. Just end each one with a semicolon:    

```
mysql> SELECT VERSION(); SELECT NOW();
+-----------+
| VERSION() |
+-----------+
| 8.0.13    |
+-----------+
1 row in set (0.00 sec)

+---------------------+
| NOW()f  |
+---------------------+
| 2018-08-24 00:56:40 |
+---------------------+
1 row in set (0.00 sec)
```

​      A query need not be given all on a single line, so lengthy queries      that require several lines are not a problem.      [**mysql**](programs.md#mysql) determines where your statement ends by      looking for the terminating semicolon, not by looking for the end      of the input line. (In other words, [**mysql**](programs.md#mysql)      accepts free-format input: it collects input lines but does not      execute them until it sees the semicolon.)    

​      Here is a simple multiple-line statement:    

```
mysql> SELECT
    -> USER()
    -> ,
    -> CURRENT_DATE;
+---------------+--------------+
| USER()        | CURRENT_DATE |
+---------------+--------------+
| jon@localhost | 2018-08-24   |
+---------------+--------------+
```

​      In this example, notice how the prompt changes from      `mysql>` to `->` after you      enter the first line of a multiple-line query. This is how      [**mysql**](programs.md#mysql) indicates that it has not yet seen a      complete statement and is waiting for the rest. The prompt is your      friend, because it provides valuable feedback. If you use that      feedback, you can always be aware of what [**mysql**](programs.md#mysql)      is waiting for.    

​      If you decide you do not want to execute a query that you are in      the process of entering, cancel it by typing      `\c`:    

```
mysql> SELECT
    -> USER()
    -> \c
mysql>
```

​      Here, too, notice the prompt. It switches back to      `mysql>` after you type `\c`,      providing feedback to indicate that [**mysql**](programs.md#mysql) is      ready for a new query.    

​      The following table shows each of the prompts you may see and      summarizes what they mean about the state that      [**mysql**](programs.md#mysql) is in.



| Prompt                                                                                                       | Meaningf f f                                                                                     |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `mysql>`                                                                                                     | Ready for new queryf f f                                                                         |
| `->`                                                                                                         | Waiting for next line of multiple-line queryf                                                    |
| `'>`                                                                                                         | Waiting for next line, waiting for completion of a string that began   with a single quote (`'`) |
| `">`                                                                                                         | Waiting for next line, waiting for completion of a string that began   with a double quote (`"`) |
| ``>`     | Waiting for next line, waiting for completion of an identifier that   began with a backtick (```) |
| `/*>`                                                                                                        | Waiting for next line, waiting for completion of a comment that began   with `/*`                |

​      Multiple-line statements commonly occur by accident when you      intend to issue a query on a single line, but forget the      terminating semicolon. In this case, [**mysql**](programs.md#mysql)      waits for more input:    

```
mysql> SELECT USER()
    ->
```

​      If this happens to you (you think you've entered a statement but      the only response is a `->` prompt), most      likely [**mysql**](programs.md#mysql) is waiting for the semicolon. If      you don't notice what the prompt is telling you, you might sit      there for a while before realizing what you need to do. Enter a      semicolon to complete the statement, and [**mysql**](programs.md#mysql)      executes it:    

```
mysql> SELECT USER()
    -> ;
+---------------+
| USER()        |
+---------------+
| jon@localhost |
+---------------+
```

​      The `'>` and `">` prompts      occur during string collection (another way of saying that MySQL      is waiting for completion of a string). In MySQL, you can write      strings surrounded by either `'` or      `"` characters (for example,      `'hello'` or `"goodbye"`), and      [**mysql**](programs.md#mysql) lets you enter strings that span multiple      lines. When you see a `'>` or      `">` prompt, it means that you have entered a      line containing a string that begins with a `'`      or `"` quote character, but have not yet entered      the matching quote that terminates the string. This often      indicates that you have inadvertently left out a quote character.      For example:    

```
mysql> SELECT * FROM my_table WHERE name = 'Smith AND age < 30;
    '>
```

​      If you enter this [`SELECT`](sql-statements.md#select) statement,      then press **Enter** and wait for the result, nothing      happens. Instead of wondering why this query takes so long, notice      the clue provided by the `'>` prompt. It tells      you that [**mysql**](programs.md#mysql) expects to see the rest of an      unterminated string. (Do you see the error in the statement? The      string `'Smith` is missing the second single      quotation mark.)    

​      At this point, what do you do? The simplest thing is to cancel the      query. However, you cannot just type `\c` in this      case, because [**mysql**](programs.md#mysql) interprets it as part of      the string that it is collecting. Instead, enter the closing quote      character (so [**mysql**](programs.md#mysql) knows you've finished the      string), then type `\c`:    

```
mysql> SELECT * FROM my_table WHERE name = 'Smith AND age < 30;
    '> '\c
mysql>
```

​      The prompt changes back to `mysql>`,      indicating that [**mysql**](programs.md#mysql) is ready for a new query.    

​      The ``>` prompt is similar to the      `'>` and `">` prompts, but      indicates that you have begun but not completed a backtick-quoted      identifier.    

​      It is important to know what the `'>`,      `">`, and ``>` prompts      signify, because if you mistakenly enter an unterminated string,      any further lines you type appear to be ignored by      [**mysql**](programs.md#mysql)—including a line containing      `QUIT`. This can be quite confusing, especially      if you do not know that you need to supply the terminating quote      before you can cancel the current query.

Note

​        Multiline statements from this point on are written without the        secondary (`->` or other) prompts, to make        it easier to copy and paste the statements to try for yourself.

## 3.3 Creating and Using a Database

- [3.3.1 Creating and Selecting a Database](tutorial.md#creating-database)
- [3.3.2 Creating a Table](tutorial.md#creating-tables)
- [3.3.3 Loading Data into a Table](tutorial.md#loading-tables)
- [3.3.4 Retrieving Information from a Table](tutorial.md#retrieving-data)



​      Once you know how to enter SQL statements, you are ready to access      a database.    

​      Suppose that you have several pets in your home (your menagerie)      and you would like to keep track of various types of information      about them. You can do so by creating tables to hold your data and      loading them with the desired information. Then you can answer      different sorts of questions about your animals by retrieving data      from the tables. This section shows you how to perform the      following operations:

- ​ Create a database        
- ​ Create a table        
- ​ Load data into the table        
- ​ Retrieve data from the table in various ways        
- ​ Use multiple tables

​      The menagerie database is simple (deliberately), but it is not      difficult to think of real-world situations in which a similar      type of database might be used. For example, a database like this      could be used by a farmer to keep track of livestock, or by a      veterinarian to keep track of patient records. A menagerie      distribution containing some of the queries and sample data used      in the following sections can be obtained from the MySQL website.      It is available in both compressed **tar** file and      Zip formats at https://dev.mysql.com/doc/.    

​      Use the [`SHOW`](sql-statements.md#show) statement to find out      what databases currently exist on the server:    

```
mysql> SHOW DATABASES;
+----------+
| Database |
+----------+
| mysql    |
| test     |
| tmp      |
+----------+
```

​      The `mysql` database describes user access      privileges. The `test` database often is      available as a workspace for users to try things out.    

​      The list of databases displayed by the statement may be different      on your machine; [`SHOW DATABASES`](sql-statements.md#show-databases)      does not show databases that you have no privileges for if you do      not have the [`SHOW DATABASES`](sql-statements.md#show-databases)      privilege. See [Section 13.7.7.14, “SHOW DATABASES Statement”](sql-statements.md#show-databases).    

​      If the `test` database exists, try to access it:    

```
mysql> USE test
Database changed
```

​      [`USE`](sql-statements.md#use), like `QUIT`,      does not require a semicolon. (You can terminate such statements      with a semicolon if you like; it does no harm.) The      [`USE`](sql-statements.md#use) statement is special in another      way, too: it must be given on a single line.    

​      You can use the `test` database (if you have      access to it) for the examples that follow, but anything you      create in that database can be removed by anyone else with access      to it. For this reason, you should probably ask your MySQL      administrator for permission to use a database of your own.      Suppose that you want to call yours `menagerie`.      The administrator needs to execute a statement like this:    

```
mysql> GRANT ALL ON menagerie.* TO 'your_mysql_name'@'your_client_host';
```

​      where `your_mysql_name` is the MySQL user name      assigned to you and `your_client_host` is the      host from which you connect to the server.

### 3.3.1 Creating and Selecting a Database



​        If the administrator creates your database for you when setting        up your permissions, you can begin using it. Otherwise, you need        to create it yourself:      

```
mysql> CREATE DATABASE menagerie;
```

​        Under Unix, database names are case-sensitive (unlike SQL        keywords), so you must always refer to your database as        `menagerie`, not as        `Menagerie`, `MENAGERIE`, or        some other variant. This is also true for table names. (Under        Windows, this restriction does not apply, although you must        refer to databases and tables using the same lettercase        throughout a given query. However, for a variety of reasons, the        recommended best practice is always to use the same lettercase        that was used when the database was created.)

Note

​ If you get an error such as ERROR 1044 (42000): Access denied for user 'micah'@'localhost' to database 'menagerie' when attempting to create a database, this means that your user account does not have the necessary privileges to do so. Discuss this with the administrator or see [Section 6.2, “Access Control and Account Management”](security.md#access-control).

​        Creating a database does not select it for use; you must do that        explicitly. To make `menagerie` the current        database, use this statement:      

```
mysql> USE menagerie
Database changed
```

​        Your database needs to be created only once, but you must select        it for use each time you begin a [**mysql**](programs.md#mysql)        session. You can do this by issuing a        [`USE`](sql-statements.md#use) statement as shown in the        example. Alternatively, you can select the database on the        command line when you invoke [**mysql**](programs.md#mysql). Just        specify its name after any connection parameters that you might        need to provide. For example:      

```
shell> mysql -h host -u user -p menagerie
Enter password: ********
```

Important

​ `menagerie` in the command just shown is **not** your password. If you want to supply your password on the command line after the `-p` option, you must do so with no intervening space (for example, as `-p*`password`*`, not as `-p *`password`*`). However, putting your password on the command line is not recommended, because doing so exposes it to snooping by other users logged in on your machine.

Note

​ You can see at any time which database is currently selected using [`SELECT`](sql-statements.md#select) [`DATABASE()`](functions.md#function_database).

### 3.3.2 Creating a Table



​        Creating the database is the easy part, but at this point it is        empty, as [`SHOW TABLES`](sql-statements.md#show-tables) tells you:      

```
mysql> SHOW TABLES;
Empty set (0.00 sec)
```

​        The harder part is deciding what the structure of your database        should be: what tables you need and what columns should be in        each of them.      

​        You want a table that contains a record for each of your pets.        This can be called the `pet` table, and it        should contain, as a bare minimum, each animal's name. Because        the name by itself is not very interesting, the table should        contain other information. For example, if more than one person        in your family keeps pets, you might want to list each animal's        owner. You might also want to record some basic descriptive        information such as species and sex.      

​        How about age? That might be of interest, but it is not a good        thing to store in a database. Age changes as time passes, which        means you'd have to update your records often. Instead, it is        better to store a fixed value such as date of birth. Then,        whenever you need age, you can calculate it as the difference        between the current date and the birth date. MySQL provides        functions for doing date arithmetic, so this is not difficult.        Storing birth date rather than age has other advantages, too:

- ​   You can use the database for tasks such as generating   reminders for upcoming pet birthdays. (If you think this   type of query is somewhat silly, note that it is the same   question you might ask in the context of a business database   to identify clients to whom you need to send out birthday   greetings in the current week or month, for that   computer-assisted personal touch.) 
- ​   You can calculate age in relation to dates other than the   current date. For example, if you store death date in the   database, you can easily calculate how old a pet was when it   died.

​        You can probably think of other types of information that would        be useful in the `pet` table, but the ones        identified so far are sufficient: name, owner, species, sex,        birth, and death.      

​        Use a [`CREATE TABLE`](sql-statements.md#create-table) statement to        specify the layout of your table:      

```
mysql> CREATE TABLE pet (name VARCHAR(20), owner VARCHAR(20),
       species VARCHAR(20), sex CHAR(1), birth DATE, death DATE);
```

​        [`VARCHAR`](data-types.md#char) is a good choice for the        `name`, `owner`, and        `species` columns because the column values        vary in length. The lengths in those column definitions need not        all be the same, and need not be `20`. You can        normally pick any length from `1` to        `65535`, whatever seems most reasonable to you.        If you make a poor choice and it turns out later that you need a        longer field, MySQL provides an [`ALTER         TABLE`](sql-statements.md#alter-table) statement.      

​        Several types of values can be chosen to represent sex in animal        records, such as `'m'` and        `'f'`, or perhaps `'male'` and        `'female'`. It is simplest to use the single        characters `'m'` and `'f'`.      

​        The use of the [`DATE`](data-types.md#datetime) data type for        the `birth` and `death`        columns is a fairly obvious choice.      

​        Once you have created a table, [`SHOW         TABLES`](sql-statements.md#show-tables) should produce some output:      

```
mysql> SHOW TABLES;
+---------------------+
| Tables in menagerie |
+---------------------+
| petf    |
+---------------------+
```

​        To verify that your table was created the way you expected, use        a [`DESCRIBE`](sql-statements.md#describe) statement:      

```
mysql> DESCRIBE pet;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name    | varchar(20) | YES  |     | NULL    |       |
| owner   | varchar(20) | YES  |     | NULL    |       |
| species | varchar(20) | YES  |     | NULL    |       |
| sex     | char(1)     | YES  |     | NULL    |       |
| birth   | date        | YES  |     | NULL    |       |
| death   | date        | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
```

​        You can use [`DESCRIBE`](sql-statements.md#describe) any time,        for example, if you forget the names of the columns in your        table or what types they have.      

​        For more information about MySQL data types, see        [Chapter 11, *Data Types*](data-types.md).

### 3.3.3 Loading Data into a Table



​        After creating your table, you need to populate it. The        [`LOAD DATA`](sql-statements.md#load-data) and        [`INSERT`](sql-statements.md#insert) statements are useful for        this.      

​        Suppose that your pet records can be described as shown here.        (Observe that MySQL expects dates in        `'*`YYYY-MM-DD`*'`        format; this may differ from what you are used to.)

| name     | owner  | species | sex | birth      | death      |
| -------- | ------ | ------- | --- | ---------- | ---------- |
| Fluffy   | Harold | cat     | f   | 1993-02-04 |            |
| Claws    | Gwen   | cat     | m   | 1994-03-17 |            |
| Buffy    | Harold | dog     | f   | 1989-05-13 |            |
| Fang     | Benny  | dog     | m   | 1990-08-27 |            |
| Bowser   | Diane  | dog     | m   | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f   | 1998-09-11 |            |
| Whistler | Gwen   | bird    |     | 1997-12-09 |            |
| Slim     | Benny  | snake   | m   | 1996-04-29 |            |

​        Because you are beginning with an empty table, an easy way to        populate it is to create a text file containing a row for each        of your animals, then load the contents of the file into the        table with a single statement.      

​        You could create a text file `pet.txt`        containing one record per line, with values separated by tabs,        and given in the order in which the columns were listed in the        [`CREATE TABLE`](sql-statements.md#create-table) statement. For        missing values (such as unknown sexes or death dates for animals        that are still living), you can use `NULL`        values. To represent these in your text file, use        `\N` (backslash, capital-N). For example, the        record for Whistler the bird would look like this (where the        whitespace between values is a single tab character):      

```
Whistler        Gwen    bird    \N      1997-12-09      \N
```

​        To load the text file `pet.txt` into the        `pet` table, use this statement:      

```
mysql> LOAD DATA LOCAL INFILE '/path/pet.txt' INTO TABLE pet;
```

​        If you created the file on Windows with an editor that uses        `\r\n` as a line terminator, you should use        this statement instead:      

```
mysql> LOAD DATA LOCAL INFILE '/path/pet.txt' INTO TABLE pet
       LINES TERMINATED BY '\r\n';
```

​        (On an Apple machine running macOS, you would likely want to use        `LINES TERMINATED BY '\r'`.)      

​        You can specify the column value separator and end of line        marker explicitly in the [`LOAD         DATA`](sql-statements.md#load-data) statement if you wish, but the defaults are tab        and linefeed. These are sufficient for the statement to read the        file `pet.txt` properly.      

​        If the statement fails, it is likely that your MySQL        installation does not have local file capability enabled by        default. See [Section 6.1.6, “Security Considerations for LOAD DATA LOCAL”](security.md#load-data-local-security), for        information on how to change this.      

​        When you want to add new records one at a time, the        [`INSERT`](sql-statements.md#insert) statement is useful. In        its simplest form, you supply values for each column, in the        order in which the columns were listed in the        [`CREATE TABLE`](sql-statements.md#create-table) statement. Suppose        that Diane gets a new hamster named “Puffball.” You        could add a new record using an        [`INSERT`](sql-statements.md#insert) statement like this:      

```
mysql> INSERT INTO pet
       VALUES ('Puffball','Diane','hamster','f','1999-03-30',NULL);
```

​        String and date values are specified as quoted strings here.        Also, with [`INSERT`](sql-statements.md#insert), you can insert        `NULL` directly to represent a missing value.        You do not use `\N` like you do with        [`LOAD DATA`](sql-statements.md#load-data).      

​        From this example, you should be able to see that there would be        a lot more typing involved to load your records initially using        several [`INSERT`](sql-statements.md#insert) statements rather        than a single [`LOAD DATA`](sql-statements.md#load-data)        statement.

### 3.3.4 Retrieving Information from a Table

- [3.3.4.1 Selecting All Data](tutorial.md#selecting-all)
- [3.3.4.2 Selecting Particular Rows](tutorial.md#selecting-rows)
- [3.3.4.3 Selecting Particular Columns](tutorial.md#selecting-columns)
- [3.3.4.4 Sorting Rows](tutorial.md#sorting-rows)
- [3.3.4.5 Date Calculations](tutorial.md#date-calculations)
- [3.3.4.6 Working with NULL Values](tutorial.md#working-with-null)
- [3.3.4.7 Pattern Matching](tutorial.md#pattern-matching)
- [3.3.4.8 Counting Rows](tutorial.md#counting-rows)
- [3.3.4.9 Using More Than one Table](tutorial.md#multiple-tables)



​        The [`SELECT`](sql-statements.md#select) statement is used to        pull information from a table. The general form of the statement        is:      

```
SELECT what_to_select
FROM which_table
WHERE conditions_to_satisfy;
```

​        *`what_to_select`* indicates what you        want to see. This can be a list of columns, or        `*` to indicate “all columns.”        *`which_table`* indicates the table from        which you want to retrieve data. The `WHERE`        clause is optional. If it is present,        *`conditions_to_satisfy`* specifies one        or more conditions that rows must satisfy to qualify for        retrieval.

#### 3.3.4.1 Selecting All Data

​ The simplest form of [`SELECT`](sql-statements.md#select) retrieves everything from a table:        

```
mysql> SELECT * FROM pet;
+----------+--------+---------+------+------------+------------+
| name     | owner  | species | sex  | birth      | death      |
+----------+--------+---------+------+------------+------------+
| Fluffy   | Harold | cat     | f    | 1993-02-04 | NULL       |
| Claws    | Gwen   | cat     | m    | 1994-03-17 | NULL       |
| Buffy    | Harold | dog     | f    | 1989-05-13 | NULL       |
| Fang     | Benny  | dog     | m    | 1990-08-27 | NULL       |
| Bowser   | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
| Chirpy   | Gwen   | bird    | f    | 1998-09-11 | NULL       |
| Whistler | Gwen   | bird    | NULL | 1997-12-09 | NULL       |
| Slim     | Benny  | snake   | m    | 1996-04-29 | NULL       |
| Puffball | Diane  | hamster | f    | 1999-03-30 | NULL       |
+----------+--------+---------+------+------------+------------+
```

​ This form of [`SELECT`](sql-statements.md#select) is useful if you want to review your entire table, for example, after you've just loaded it with your initial data set. For example, you may happen to think that the birth date for Bowser doesn't seem quite right. Consulting your original pedigree papers, you find that the correct birth year should be 1989, not 1979.        

​ There are at least two ways to fix this:

- ​f Edit the file `pet.txt` to correct thef error, then empty the table and reload it usingf [`DELETE`](sql-statements.md#delete) andf [`LOAD DATA`](sql-statements.md#load-data):   

  ```
  mysql> DELETE FROM pet;
  mysql> LOAD DATA LOCAL INFILE 'pet.txt' INTO TABLE pet;
  ```

  ​f However, if you do this, you must also re-enter the recordf for Puffball.   

- ​f Fix only the erroneous record with anf [`UPDATE`](sql-statements.md#update) statement:   

  ```
  mysql> UPDATE pet SET birth = '1989-08-31' WHERE name = 'Bowser';
  ```

  ​f The [`UPDATE`](sql-statements.md#update) changes only thef record in question and does not require you to reload thef table.

#### 3.3.4.2 Selecting Particular Rows



​ As shown in the preceding section, it is easy to retrieve an entire table. Just omit the `WHERE` clause from the [`SELECT`](sql-statements.md#select) statement. But typically you don't want to see the entire table, particularly when it becomes large. Instead, you're usually more interested in answering a particular question, in which case you specify some constraints on the information you want. Let's look at some selection queries in terms of questions about your pets that they answer.        

​ You can select only particular rows from your table. For example, if you want to verify the change that you made to Bowser's birth date, select Bowser's record like this:        

```
mysql> SELECT * FROM pet WHERE name = 'Bowser';
+--------+-------+---------+------+------------+------------+
| name   | owner | species | sex  | birth      | death      |
+--------+-------+---------+------+------------+------------+
| Bowser | Diane | dog     | m    | 1989-08-31 | 1995-07-29 |
+--------+-------+---------+------+------------+------------+
```

​ The output confirms that the year is correctly recorded as 1989, not 1979.        

​ String comparisons normally are case-insensitive, so you can specify the name as `'bowser'`, `'BOWSER'`, and so forth. The query result is the same.        

​ You can specify conditions on any column, not just `name`. For example, if you want to know which animals were born during or after 1998, test the `birth` column:        

```
mysql> SELECT * FROM pet WHERE birth >= '1998-1-1';
+----------+-------+---------+------+------------+-------+
| name     | owner | species | sex  | birth      | death |
+----------+-------+---------+------+------------+-------+
| Chirpy   | Gwen  | bird    | f    | 1998-09-11 | NULL  |
| Puffball | Diane | hamster | f    | 1999-03-30 | NULL  |
+----------+-------+---------+------+------------+-------+
```

​ You can combine conditions, for example, to locate female dogs:        

```
mysql> SELECT * FROM pet WHERE species = 'dog' AND sex = 'f';
+-------+--------+---------+------+------------+-------+
| name  | owner  | species | sex  | birth      | death |
+-------+--------+---------+------+------------+-------+
| Buffy | Harold | dog     | f    | 1989-05-13 | NULL  |
+-------+--------+---------+------+------------+-------+
```

​ The preceding query uses the [`AND`](functions.md#operator_and) logical operator. There is also an [`OR`](functions.md#operator_or) operator:        

```
mysql> SELECT * FROM pet WHERE species = 'snake' OR species = 'bird';
+----------+-------+---------+------+------------+-------+
| name     | owner | species | sex  | birth      | death |
+----------+-------+---------+------+------------+-------+
| Chirpy   | Gwen  | bird    | f    | 1998-09-11 | NULL  |
| Whistler | Gwen  | bird    | NULL | 1997-12-09 | NULL  |
| Slim     | Benny | snake   | m    | 1996-04-29 | NULL  |
+----------+-------+---------+------+------------+-------+
```

​ [`AND`](functions.md#operator_and) and [`OR`](functions.md#operator_or) may be intermixed, although [`AND`](functions.md#operator_and) has higher precedence than [`OR`](functions.md#operator_or). If you use both operators, it is a good idea to use parentheses to indicate explicitly how conditions should be grouped:        

```
mysql> SELECT * FROM pet WHERE (species = 'cat' AND sex = 'm')
       OR (species = 'dog' AND sex = 'f');
+-------+--------+---------+------+------------+-------+
| name  | owner  | species | sex  | birth      | death |
+-------+--------+---------+------+------------+-------+
| Claws | Gwen   | cat     | m    | 1994-03-17 | NULL  |
| Buffy | Harold | dog     | f    | 1989-05-13 | NULL  |
+-------+--------+---------+------+------------+-------+
```

#### 3.3.4.3 Selecting Particular Columns



​ If you do not want to see entire rows from your table, just name the columns in which you are interested, separated by commas. For example, if you want to know when your animals were born, select the `name` and `birth` columns:        

```
mysql> SELECT name, birth FROM pet;
+----------+------------+
| name     | birth      |
+----------+------------+
| Fluffy   | 1993-02-04 |
| Claws    | 1994-03-17 |
| Buffy    | 1989-05-13 |
| Fang     | 1990-08-27 |
| Bowser   | 1989-08-31 |
| Chirpy   | 1998-09-11 |
| Whistler | 1997-12-09 |
| Slim     | 1996-04-29 |
| Puffball | 1999-03-30 |
+----------+------------+
```

​ To find out who owns pets, use this query:        

```
mysql> SELECT owner FROM pet;
+--------+
| owner  |
+--------+
| Harold |
| Gwen   |
| Harold |
| Benny  |
| Diane  |
| Gwen   |
| Gwen   |
| Benny  |
| Diane  |
+--------+
```



​ Notice that the query simply retrieves the `owner` column from each record, and some of them appear more than once. To minimize the output, retrieve each unique output record just once by adding the keyword `DISTINCT`:        

```
mysql> SELECT DISTINCT owner FROM pet;
+--------+
| owner  |
+--------+
| Benny  |
| Diane  |
| Gwen   |
| Harold |
+--------+
```

​ You can use a `WHERE` clause to combine row selection with column selection. For example, to get birth dates for dogs and cats only, use this query:        

```
mysql> SELECT name, species, birth FROM pet
       WHERE species = 'dog' OR species = 'cat';
+--------+---------+------------+
| name   | species | birth      |
+--------+---------+------------+
| Fluffy | cat     | 1993-02-04 |
| Claws  | cat     | 1994-03-17 |
| Buffy  | dog     | 1989-05-13 |
| Fang   | dog     | 1990-08-27 |
| Bowser | dog     | 1989-08-31 |
+--------+---------+------------+
```

#### 3.3.4.4 Sorting Rows



​ You may have noticed in the preceding examples that the result rows are displayed in no particular order. It is often easier to examine query output when the rows are sorted in some meaningful way. To sort a result, use an `ORDER BY` clause.        

​ Here are animal birthdays, sorted by date:        

```
mysql> SELECT name, birth FROM pet ORDER BY birth;
+----------+------------+
| name     | birth      |
+----------+------------+
| Buffy    | 1989-05-13 |
| Bowser   | 1989-08-31 |
| Fang     | 1990-08-27 |
| Fluffy   | 1993-02-04 |
| Claws    | 1994-03-17 |
| Slim     | 1996-04-29 |
| Whistler | 1997-12-09 |
| Chirpy   | 1998-09-11 |
| Puffball | 1999-03-30 |
+----------+------------+
```

​ On character type columns, sorting—like all other comparison operations—is normally performed in a case-insensitive fashion. This means that the order is undefined for columns that are identical except for their case. You can force a case-sensitive sort for a column by using [`BINARY`](functions.md#operator_binary) like so: `ORDER BY BINARY *`col_name`*`.        

​ The default sort order is ascending, with smallest values first. To sort in reverse (descending) order, add the `DESC` keyword to the name of the column you are sorting by:        

```
mysql> SELECT name, birth FROM pet ORDER BY birth DESC;
+----------+------------+
| name     | birth      |
+----------+------------+
| Puffball | 1999-03-30 |
| Chirpy   | 1998-09-11 |
| Whistler | 1997-12-09 |
| Slim     | 1996-04-29 |
| Claws    | 1994-03-17 |
| Fluffy   | 1993-02-04 |
| Fang     | 1990-08-27 |
| Bowser   | 1989-08-31 |
| Buffy    | 1989-05-13 |
+----------+------------+
```

​ You can sort on multiple columns, and you can sort different columns in different directions. For example, to sort by type of animal in ascending order, then by birth date within animal type in descending order (youngest animals first), use the following query:        

```
mysql> SELECT name, species, birth FROM pet
       ORDER BY species, birth DESC;
+----------+---------+------------+
| name     | species | birth      |
+----------+---------+------------+
| Chirpy   | bird    | 1998-09-11 |
| Whistler | bird    | 1997-12-09 |
| Claws    | cat     | 1994-03-17 |
| Fluffy   | cat     | 1993-02-04 |
| Fang     | dog     | 1990-08-27 |
| Bowser   | dog     | 1989-08-31 |
| Buffy    | dog     | 1989-05-13 |
| Puffball | hamster | 1999-03-30 |
| Slim     | snake   | 1996-04-29 |
+----------+---------+------------+
```

​ The `DESC` keyword applies only to the column name immediately preceding it (`birth`); it does not affect the `species` column sort order.

#### 3.3.4.5 Date Calculations



​ MySQL provides several functions that you can use to perform calculations on dates, for example, to calculate ages or extract parts of dates.        

​ To determine how many years old each of your pets is, use the [`TIMESTAMPDIFF()`](functions.md#function_timestampdiff) function. Its arguments are the unit in which you want the result expressed, and the two dates for which to take the difference. The following query shows, for each pet, the birth date, the current date, and the age in years. An *alias* (`age`) is used to make the final output column label more meaningful.        

```
mysql> SELECT name, birth, CURDATE(),
       TIMESTAMPDIFF(YEAR,birth,CURDATE()) AS age
       FROM pet;
+----------+------------+------------+------+
| name     | birth      | CURDATE()  | age  |
+----------+------------+------------+------+
| Fluffy   | 1993-02-04 | 2003-08-19 |   10 |
| Claws    | 1994-03-17 | 2003-08-19 |    9 |
| Buffy    | 1989-05-13 | 2003-08-19 |   14 |
| Fang     | 1990-08-27 | 2003-08-19 |   12 |
| Bowser   | 1989-08-31 | 2003-08-19 |   13 |
| Chirpy   | 1998-09-11 | 2003-08-19 |    4 |
| Whistler | 1997-12-09 | 2003-08-19 |    5 |
| Slim     | 1996-04-29 | 2003-08-19 |    7 |
| Puffball | 1999-03-30 | 2003-08-19 |    4 |
+----------+------------+------------+------+
```

​ The query works, but the result could be scanned more easily if the rows were presented in some order. This can be done by adding an `ORDER BY name` clause to sort the output by name:        

```
mysql> SELECT name, birth, CURDATE(),
       TIMESTAMPDIFF(YEAR,birth,CURDATE()) AS age
       FROM pet ORDER BY name;
+----------+------------+------------+------+
| name     | birth      | CURDATE()  | age  |
+----------+------------+------------+------+
| Bowser   | 1989-08-31 | 2003-08-19 |   13 |
| Buffy    | 1989-05-13 | 2003-08-19 |   14 |
| Chirpy   | 1998-09-11 | 2003-08-19 |    4 |
| Claws    | 1994-03-17 | 2003-08-19 |    9 |
| Fang     | 1990-08-27 | 2003-08-19 |   12 |
| Fluffy   | 1993-02-04 | 2003-08-19 |   10 |
| Puffball | 1999-03-30 | 2003-08-19 |    4 |
| Slim     | 1996-04-29 | 2003-08-19 |    7 |
| Whistler | 1997-12-09 | 2003-08-19 |    5 |
+----------+------------+------------+------+
```

​ To sort the output by `age` rather than `name`, just use a different `ORDER BY` clause:        

```
mysql> SELECT name, birth, CURDATE(),
       TIMESTAMPDIFF(YEAR,birth,CURDATE()) AS age
       FROM pet ORDER BY age;
+----------+------------+------------+------+
| name     | birth      | CURDATE()  | age  |
+----------+------------+------------+------+
| Chirpy   | 1998-09-11 | 2003-08-19 |    4 |
| Puffball | 1999-03-30 | 2003-08-19 |    4 |
| Whistler | 1997-12-09 | 2003-08-19 |    5 |
| Slim     | 1996-04-29 | 2003-08-19 |    7 |
| Claws    | 1994-03-17 | 2003-08-19 |    9 |
| Fluffy   | 1993-02-04 | 2003-08-19 |   10 |
| Fang     | 1990-08-27 | 2003-08-19 |   12 |
| Bowser   | 1989-08-31 | 2003-08-19 |   13 |
| Buffy    | 1989-05-13 | 2003-08-19 |   14 |
+----------+------------+------------+------+
```

​ A similar query can be used to determine age at death for animals that have died. You determine which animals these are by checking whether the `death` value is `NULL`. Then, for those with non-`NULL` values, compute the difference between the `death` and `birth` values:        

```
mysql> SELECT name, birth, death,
       TIMESTAMPDIFF(YEAR,birth,death) AS age
       FROM pet WHERE death IS NOT NULL ORDER BY age;
+--------+------------+------------+------+
| name   | birth      | death      | age  |
+--------+------------+------------+------+
| Bowser | 1989-08-31 | 1995-07-29 |    5 |
+--------+------------+------------+------+
```

​ The query uses `death IS NOT NULL` rather than `death <> NULL` because `NULL` is a special value that cannot be compared using the usual comparison operators. This is discussed later. See [Section 3.3.4.6, “Working with NULL Values”](tutorial.md#working-with-null).        

​ What if you want to know which animals have birthdays next month? For this type of calculation, year and day are irrelevant; you simply want to extract the month part of the `birth` column. MySQL provides several functions for extracting parts of dates, such as [`YEAR()`](functions.md#function_year), [`MONTH()`](functions.md#function_month), and [`DAYOFMONTH()`](functions.md#function_dayofmonth). [`MONTH()`](functions.md#function_month) is the appropriate function here. To see how it works, run a simple query that displays the value of both `birth` and [`MONTH(birth)`](functions.md#function_month):        

```
mysql> SELECT name, birth, MONTH(birth) FROM pet;
+----------+------------+--------------+
| name     | birth      | MONTH(birth) |
+----------+------------+--------------+
| Fluffy   | 1993-02-04 |   2 |
| Claws    | 1994-03-17 |   3 |
| Buffy    | 1989-05-13 |   5 |
| Fang     | 1990-08-27 |   8 |
| Bowser   | 1989-08-31 |   8 |
| Chirpy   | 1998-09-11 |   9 |
| Whistler | 1997-12-09 |  12 |
| Slim     | 1996-04-29 |   4 |
| Puffball | 1999-03-30 |   3 |
+----------+------------+--------------+
```

​ Finding animals with birthdays in the upcoming month is also simple. Suppose that the current month is April. Then the month value is `4` and you can look for animals born in May (month `5`) like this:        

```
mysql> SELECT name, birth FROM pet WHERE MONTH(birth) = 5;
+-------+------------+
| name  | birth      |
+-------+------------+
| Buffy | 1989-05-13 |
+-------+------------+
```

​ There is a small complication if the current month is December. You cannot merely add one to the month number (`12`) and look for animals born in month `13`, because there is no such month. Instead, you look for animals born in January (month `1`).        

​ You can write the query so that it works no matter what the current month is, so that you do not have to use the number for a particular month. [`DATE_ADD()`](functions.md#function_date-add) enables you to add a time interval to a given date. If you add a month to the value of [`CURDATE()`](functions.md#function_curdate), then extract the month part with [`MONTH()`](functions.md#function_month), the result produces the month in which to look for birthdays:        

```
mysql> SELECT name, birth FROM pet
       WHERE MONTH(birth) = MONTH(DATE_ADD(CURDATE(),INTERVAL 1 MONTH));
```

​ A different way to accomplish the same task is to add `1` to get the next month after the current one after using the modulo function (`MOD`) to wrap the month value to `0` if it is currently `12`:        

```
mysql> SELECT name, birth FROM pet
       WHERE MONTH(birth) = MOD(MONTH(CURDATE()), 12) + 1;
```

​ [`MONTH()`](functions.md#function_month) returns a number between `1` and `12`. And [`MOD(something,12)`](functions.md#function_mod) returns a number between `0` and `11`. So the addition has to be after the [`MOD()`](functions.md#function_mod), otherwise we would go from November (`11`) to January (`1`).        

​ If a calculation uses invalid dates, the calculation fails and produces warnings:        

```
mysql> SELECT '2018-10-31' + INTERVAL 1 DAY;
+-------------------------------+
| '2018-10-31' + INTERVAL 1 DAY |
+-------------------------------+
| 2018-11-01f       |
+-------------------------------+
mysql> SELECT '2018-10-32' + INTERVAL 1 DAY;
+-------------------------------+
| '2018-10-32' + INTERVAL 1 DAY |
+-------------------------------+
| NULLf    |
+-------------------------------+
mysql> SHOW WARNINGS;
+---------+------+----------------------------------------+
| Level   | Code | Messagef f     |
+---------+------+----------------------------------------+
| Warning | 1292 | Incorrect datetime value: '2018-10-32' |
+---------+------+----------------------------------------+
```

#### 3.3.4.6 Working with NULL Values



​ The `NULL` value can be surprising until you get used to it. Conceptually, `NULL` means “a missing unknown value” and it is treated somewhat differently from other values.        

​ To test for `NULL`, use the [`IS NULL`](functions.md#operator_is-null) and [`IS  NOT NULL`](functions.md#operator_is-not-null) operators, as shown here:        

```
mysql> SELECT 1 IS NULL, 1 IS NOT NULL;
+-----------+---------------+
| 1 IS NULL | 1 IS NOT NULL |
+-----------+---------------+
|         0 |    1 |
+-----------+---------------+
```

​ You cannot use arithmetic comparison operators such as [`=`](functions.md#operator_equal), [`<`](functions.md#operator_less-than), or [`<>`](functions.md#operator_not-equal) to test for `NULL`. To demonstrate this for yourself, try the following query:        

```
mysql> SELECT 1 = NULL, 1 <> NULL, 1 < NULL, 1 > NULL;
+----------+-----------+----------+----------+
| 1 = NULL | 1 <> NULL | 1 < NULL | 1 > NULL |
+----------+-----------+----------+----------+
|     NULL |      NULL |     NULL |     NULL |
+----------+-----------+----------+----------+
```

​ Because the result of any arithmetic comparison with `NULL` is also `NULL`, you cannot obtain any meaningful results from such comparisons.        

​ In MySQL, `0` or `NULL` means false and anything else means true. The default truth value from a boolean operation is `1`.        

​ This special treatment of `NULL` is why, in the previous section, it was necessary to determine which animals are no longer alive using `death IS NOT NULL` instead of `death <> NULL`.        

​ Two `NULL` values are regarded as equal in a `GROUP BY`.        

​ When doing an `ORDER BY`, `NULL` values are presented first if you do `ORDER BY ... ASC` and last if you do `ORDER BY ... DESC`.        

​ A common error when working with `NULL` is to assume that it is not possible to insert a zero or an empty string into a column defined as `NOT NULL`, but this is not the case. These are in fact values, whereas `NULL` means “not having a value.” You can test this easily enough by using `IS [NOT] NULL` as shown:        

```
mysql> SELECT 0 IS NULL, 0 IS NOT NULL, '' IS NULL, '' IS NOT NULL;
+-----------+---------------+------------+----------------+
| 0 IS NULL | 0 IS NOT NULL | '' IS NULL | '' IS NOT NULL |
+-----------+---------------+------------+----------------+
|         0 |    1 | 0 |f 1 |
+-----------+---------------+------------+----------------+
```

​ Thus it is entirely possible to insert a zero or empty string into a `NOT NULL` column, as these are in fact `NOT NULL`. See [Section B.3.4.3, “Problems with NULL Values”](error-handling.md#problems-with-null).

#### 3.3.4.7 Pattern Matching



​ MySQL provides standard SQL pattern matching as well as a form of pattern matching based on extended regular expressions similar to those used by Unix utilities such as **vi**, **grep**, and **sed**.        

​ SQL pattern matching enables you to use `_` to match any single character and `%` to match an arbitrary number of characters (including zero characters). In MySQL, SQL patterns are case-insensitive by default. Some examples are shown here. Do not use `=` or `<>` when you use SQL patterns. Use the [`LIKE`](functions.md#operator_like) or [`NOT LIKE`](functions.md#operator_not-like) comparison operators instead.        

​ To find names beginning with `b`:        

```
mysql> SELECT * FROM pet WHERE name LIKE 'b%';
+--------+--------+---------+------+------------+------------+
| name   | owner  | species | sex  | birth      | death      |
+--------+--------+---------+------+------------+------------+
| Buffy  | Harold | dog     | f    | 1989-05-13 | NULL       |
| Bowser | Diane  | dog     | m    | 1989-08-31 | 1995-07-29 |
+--------+--------+---------+------+------------+------------+
```

​ To find names ending with `fy`:        

```
mysql> SELECT * FROM pet WHERE name LIKE '%fy';
+--------+--------+---------+------+------------+-------+
| name   | owner  | species | sex  | birth      | death |
+--------+--------+---------+------+------------+-------+
| Fluffy | Harold | cat     | f    | 1993-02-04 | NULL  |
| Buffy  | Harold | dog     | f    | 1989-05-13 | NULL  |
+--------+--------+---------+------+------------+-------+
```

​ To find names containing a `w`:        

```
mysql> SELECT * FROM pet WHERE name LIKE '%w%';
+----------+-------+---------+------+------------+------------+
| name     | owner | species | sex  | birth      | death      |
+----------+-------+---------+------+------------+------------+
| Claws    | Gwen  | cat     | m    | 1994-03-17 | NULL       |
| Bowser   | Diane | dog     | m    | 1989-08-31 | 1995-07-29 |
| Whistler | Gwen  | bird    | NULL | 1997-12-09 | NULL       |
+----------+-------+---------+------+------------+------------+
```

​ To find names containing exactly five characters, use five instances of the `_` pattern character:        

```
mysql> SELECT * FROM pet WHERE name LIKE '_____';
+-------+--------+---------+------+------------+-------+
| name  | owner  | species | sex  | birth      | death |
+-------+--------+---------+------+------------+-------+
| Claws | Gwen   | cat     | m    | 1994-03-17 | NULL  |
| Buffy | Harold | dog     | f    | 1989-05-13 | NULL  |
+-------+--------+---------+------+------------+-------+
```

​ The other type of pattern matching provided by MySQL uses extended regular expressions. When you test for a match for this type of pattern, use the [`REGEXP_LIKE()`](functions.md#function_regexp-like) function (or the [`REGEXP`](functions.md#operator_regexp) or [`RLIKE`](functions.md#operator_regexp) operators, which are synonyms for [`REGEXP_LIKE()`](functions.md#function_regexp-like)).        

​ The following list describes some characteristics of extended regular expressions:

- ​f `.` matches any single character.   
- ​f A character class `[...]` matches anyf character within the brackets. For example,f `[abc]` matches `a`,f `b`, or `c`. To name af range of characters, use a dash. `[a-z]`f matches any letter, whereas `[0-9]`f matches any digit.   
- ​f `*` matches zero or more instances of thef thing preceding it. For example, `x*`f matches any number of `x` characters,f `[0-9]*` matches any number of digits,f and `.*` matches any number of anything.   
- ​f A regular expression pattern match succeeds if the patternf matches anywhere in the value being tested. (This differsf from a [`LIKE`](functions.md#operator_like) pattern match,f which succeeds only if the pattern matches the entiref value.)   
- ​f To anchor a pattern so that it must match the beginning orf end of the value being tested, use `^` atf the beginning or `$` at the end of thef pattern.

​ To demonstrate how extended regular expressions work, the [`LIKE`](functions.md#operator_like) queries shown previously are rewritten here to use [`REGEXP_LIKE()`](functions.md#function_regexp-like).        

​ To find names beginning with `b`, use `^` to match the beginning of the name:        

```
mysql> SELECT * FROM pet WHERE REGEXP_LIKE(name, '^b');
+--------+--------+---------+------+------------+------------+
| name   | owner  | species | sex  | birth      | death      |
+--------+--------+---------+------+------------+------------+
| Buffy  | Harold | dog     | f    | 1989-05-13 | NULL       |
| Bowser | Diane  | dog     | m    | 1979-08-31 | 1995-07-29 |
+--------+--------+---------+------+------------+------------+
```

​ To force a regular expression comparison to be case sensitive, use a case-sensitive collation, or use the [`BINARY`](functions.md#operator_binary) keyword to make one of the strings a binary string, or specify the `c` match-control character. Each of these queries matches only lowercase `b` at the beginning of a name:        

```
SELECT * FROM pet WHERE REGEXP_LIKE(name, '^b' COLLATE utf8mb4_0900_as_cs);
SELECT * FROM pet WHERE REGEXP_LIKE(name, BINARY '^b');
SELECT * FROM pet WHERE REGEXP_LIKE(name, '^b', 'c');
```

​ To find names ending with `fy`, use `$` to match the end of the name:        

```
mysql> SELECT * FROM pet WHERE REGEXP_LIKE(name, 'fy$');
+--------+--------+---------+------+------------+-------+
| name   | owner  | species | sex  | birth      | death |
+--------+--------+---------+------+------------+-------+
| Fluffy | Harold | cat     | f    | 1993-02-04 | NULL  |
| Buffy  | Harold | dog     | f    | 1989-05-13 | NULL  |
+--------+--------+---------+------+------------+-------+
```

​ To find names containing a `w`, use this query:        

```
mysql> SELECT * FROM pet WHERE REGEXP_LIKE(name, 'w');
+----------+-------+---------+------+------------+------------+
| name     | owner | species | sex  | birth      | death      |
+----------+-------+---------+------+------------+------------+
| Claws    | Gwen  | cat     | m    | 1994-03-17 | NULL       |
| Bowser   | Diane | dog     | m    | 1989-08-31 | 1995-07-29 |
| Whistler | Gwen  | bird    | NULL | 1997-12-09 | NULL       |
+----------+-------+---------+------+------------+------------+
```

​ Because a regular expression pattern matches if it occurs anywhere in the value, it is not necessary in the previous query to put a wildcard on either side of the pattern to get it to match the entire value as would be true with an SQL pattern.        

​ To find names containing exactly five characters, use `^` and `$` to match the beginning and end of the name, and five instances of `.` in between:        

```
mysql> SELECT * FROM pet WHERE REGEXP_LIKE(name, '^.....$');
+-------+--------+---------+------+------------+-------+
| name  | owner  | species | sex  | birth      | death |
+-------+--------+---------+------+------------+-------+
| Claws | Gwen   | cat     | m    | 1994-03-17 | NULL  |
| Buffy | Harold | dog     | f    | 1989-05-13 | NULL  |
+-------+--------+---------+------+------------+-------+
```

​ You could also write the previous query using the `{*`n`*}` (“repeat-*`n`*-times”) operator:        

```
mysql> SELECT * FROM pet WHERE REGEXP_LIKE(name, '^.{5}$');
+-------+--------+---------+------+------------+-------+
| name  | owner  | species | sex  | birth      | death |
+-------+--------+---------+------+------------+-------+
| Claws | Gwen   | cat     | m    | 1994-03-17 | NULL  |
| Buffy | Harold | dog     | f    | 1989-05-13 | NULL  |
+-------+--------+---------+------+------------+-------+
```

​ For more information about the syntax for regular expressions, see [Section 12.7.2, “Regular Expressions”](functions.md#regexp).

#### 3.3.4.8 Counting Rows



​ Databases are often used to answer the question, “How often does a certain type of data occur in a table?” For example, you might want to know how many pets you have, or how many pets each owner has, or you might want to perform various kinds of census operations on your animals.        

​ Counting the total number of animals you have is the same question as “How many rows are in the `pet` table?” because there is one record per pet. [`COUNT(*)`](functions.md#function_count) counts the number of rows, so the query to count your animals looks like this:        

```
mysql> SELECT COUNT(*) FROM pet;
+----------+
| COUNT(*) |
+----------+
|        9 |
+----------+
```

​ Earlier, you retrieved the names of the people who owned pets. You can use [`COUNT()`](functions.md#function_count) if you want to find out how many pets each owner has:        

```
mysql> SELECT owner, COUNT(*) FROM pet GROUP BY owner;
+--------+----------+
| owner  | COUNT(*) |
+--------+----------+
| Benny  |        2 |
| Diane  |        2 |
| Gwen   |        3 |
| Harold |        2 |
+--------+----------+
```

​ The preceding query uses `GROUP BY` to group all records for each `owner`. The use of [`COUNT()`](functions.md#function_count) in conjunction with `GROUP BY` is useful for characterizing your data under various groupings. The following examples show different ways to perform animal census operations.        

​ Number of animals per species:        

```
mysql> SELECT species, COUNT(*) FROM pet GROUP BY species;
+---------+----------+
| species | COUNT(*) |
+---------+----------+
| bird    |        2 |
| cat     |        2 |
| dog     |        3 |
| hamster |        1 |
| snake   |        1 |
+---------+----------+
```

​ Number of animals per sex:        

```
mysql> SELECT sex, COUNT(*) FROM pet GROUP BY sex;
+------+----------+
| sex  | COUNT(*) |
+------+----------+
| NULL |        1 |
| f    |        4 |
| m    |        4 |
+------+----------+
```

​ (In this output, `NULL` indicates that the sex is unknown.)        

​ Number of animals per combination of species and sex:        

```
mysql> SELECT species, sex, COUNT(*) FROM pet GROUP BY species, sex;
+---------+------+----------+
| species | sex  | COUNT(*) |
+---------+------+----------+
| bird    | NULL |        1 |
| bird    | f    |        1 |
| cat     | f    |        1 |
| cat     | m    |        1 |
| dog     | f    |        1 |
| dog     | m    |        2 |
| hamster | f    |        1 |
| snake   | m    |        1 |
+---------+------+----------+
```

​ You need not retrieve an entire table when you use [`COUNT()`](functions.md#function_count). For example, the previous query, when performed just on dogs and cats, looks like this:        

```
mysql> SELECT species, sex, COUNT(*) FROM pet
       WHERE species = 'dog' OR species = 'cat'
       GROUP BY species, sex;
+---------+------+----------+
| species | sex  | COUNT(*) |
+---------+------+----------+
| cat     | f    |        1 |
| cat     | m    |        1 |
| dog     | f    |        1 |
| dog     | m    |        2 |
+---------+------+----------+
```

​ Or, if you wanted the number of animals per sex only for animals whose sex is known:        

```
mysql> SELECT species, sex, COUNT(*) FROM pet
       WHERE sex IS NOT NULL
       GROUP BY species, sex;
+---------+------+----------+
| species | sex  | COUNT(*) |
+---------+------+----------+
| bird    | f    |        1 |
| cat     | f    |        1 |
| cat     | m    |        1 |
| dog     | f    |        1 |
| dog     | m    |        2 |
| hamster | f    |        1 |
| snake   | m    |        1 |
+---------+------+----------+
```

​ If you name columns to select in addition to the [`COUNT()`](functions.md#function_count) value, a `GROUP BY` clause should be present that names those same columns. Otherwise, the following occurs:

- ​f If thef [`ONLY_FULL_GROUP_BY`](server-administration.md#sqlmode_only_full_group_by) SQLf mode is enabled, an error occurs:   

  ```
  mysql> SET sql_mode = 'ONLY_FULL_GROUP_BY';
  Query OK, 0 rows affected (0.00 sec)
  
  mysql> SELECT owner, COUNT(*) FROM pet;
  ERROR 1140 (42000): In aggregated query without GROUP BY, expression
  #1 of SELECT list contains nonaggregated column 'menagerie.pet.owner';
  this is incompatible with sql_mode=only_full_group_by
  ```

- ​f If [`ONLY_FULL_GROUP_BY`](server-administration.md#sqlmode_only_full_group_by) isf not enabled, the query is processed by treating all rowsf as a single group, but the value selected for each namedf column is nondeterministic. The server is free to selectf the value from any row:   

  ```
  mysql> SET sql_mode = '';
  Query OK, 0 rows affected (0.00 sec)
  
  mysql> SELECT owner, COUNT(*) FROM pet;
  +--------+----------+
  | owner  | COUNT(*) |
  +--------+----------+
  | Harold |        8 |
  +--------+----------+
  1 row in set (0.00 sec)
  ```

​ See also [Section 12.20.3, “MySQL Handling of GROUP BY”](functions.md#group-by-handling). See [Section 12.20.1, “Aggregate Function Descriptions”](functions.md#aggregate-functions) for information about [`COUNT(*`expr`*)`](functions.md#function_count) behavior and related optimizations.

#### 3.3.4.9 Using More Than one Table



​ The `pet` table keeps track of which pets you have. If you want to record other information about them, such as events in their lives like visits to the vet or when litters are born, you need another table. What should this table look like? It needs to contain the following information:

- ​f The pet name so that you know which animal each eventf pertains to.   
- ​f A date so that you know when the event occurred.   
- ​f A field to describe the event.   
- ​f An event type field, if you want to be able to categorizef events.

​ Given these considerations, the [`CREATE  TABLE`](sql-statements.md#create-table) statement for the `event` table might look like this:        

```
mysql> CREATE TABLE event (name VARCHAR(20), date DATE,
       type VARCHAR(15), remark VARCHAR(255));
```

​ As with the `pet` table, it is easiest to load the initial records by creating a tab-delimited text file containing the following information.

| name     | date       | type     | remarkf                     |
| -------- | ---------- | -------- | --------------------------- |
| Fluffy   | 1995-05-15 | litter   | 4 kittens, 3 female, 1 male |
| Buffy    | 1993-06-23 | litter   | 5 puppies, 2 female, 3 male |
| Buffy    | 1994-06-19 | litter   | 3 puppies, 3 female         |
| Chirpy   | 1999-03-21 | vet      | needed beak straightened    |
| Slim     | 1997-08-03 | vet      | broken ribf                 |
| Bowser   | 1991-10-12 | kennel   | f f                         |
| Fang     | 1991-10-12 | kennel   | f f                         |
| Fang     | 1998-08-28 | birthday | Gave him a new chew toy     |
| Claws    | 1998-03-17 | birthday | Gave him a new flea collar  |
| Whistler | 1998-12-09 | birthday | First birthdayf             |

​ Load the records like this:        

```
mysql> LOAD DATA LOCAL INFILE 'event.txt' INTO TABLE event;
```

​ Based on what you have learned from the queries that you have run on the `pet` table, you should be able to perform retrievals on the records in the `event` table; the principles are the same. But when is the `event` table by itself insufficient to answer questions you might ask?        

​ Suppose that you want to find out the ages at which each pet had its litters. We saw earlier how to calculate ages from two dates. The litter date of the mother is in the `event` table, but to calculate her age on that date you need her birth date, which is stored in the `pet` table. This means the query requires both tables:        

```
mysql> SELECT pet.name,
       TIMESTAMPDIFF(YEAR,birth,date) AS age,
       remark
       FROM pet INNER JOIN event
         ON pet.name = event.name
       WHERE event.type = 'litter';
+--------+------+-----------------------------+
| name   | age  | remarkf         |
+--------+------+-----------------------------+
| Fluffy |    2 | 4 kittens, 3 female, 1 male |
| Buffy  |    4 | 5 puppies, 2 female, 3 male |
| Buffy  |    5 | 3 puppies, 3 female         |
+--------+------+-----------------------------+
```

​ There are several things to note about this query:

- ​f The `FROM` clause joins two tablesf because the query needs to pull information from both off them.   

- ​f When combining (joining) information from multiple tables,f you need to specify how records in one table can bef matched to records in the other. This is easy because theyf both have a `name` column. The query usesf an `ON` clause to match up records in thef two tables based on the `name` values.   

  ​f The query uses an `INNER JOIN` to combinef the tables. An `INNER JOIN` permits rowsf from either table to appear in the result if and only iff both tables meet the conditions specified in thef `ON` clause. In this example, thef `ON` clause specifies that thef `name` column in thef `pet` table must match thef `name` column in thef `event` table. If a name appears in onef table but not the other, the row will not appear in thef result because the condition in the `ON`f clause fails.   

- ​f Because the `name` column occurs in bothf tables, you must be specific about which table you meanf when referring to the column. This is done by prependingf the table name to the column name.

​ You need not have two different tables to perform a join. Sometimes it is useful to join a table to itself, if you want to compare records in a table to other records in that same table. For example, to find breeding pairs among your pets, you can join the `pet` table with itself to produce candidate pairs of live males and females of like species:        

```
mysql> SELECT p1.name, p1.sex, p2.name, p2.sex, p1.species
       FROM pet AS p1 INNER JOIN pet AS p2
         ON p1.species = p2.species
         AND p1.sex = 'f' AND p1.death IS NULL
         AND p2.sex = 'm' AND p2.death IS NULL;
+--------+------+-------+------+---------+
| name   | sex  | name  | sex  | species |
+--------+------+-------+------+---------+
| Fluffy | f    | Claws | m    | cat     |
| Buffy  | f    | Fang  | m    | dog     |
+--------+------+-------+------+---------+
```

​ In this query, we specify aliases for the table name to refer to the columns and keep straight which instance of the table each column reference is associated with.

## 3.4 Getting Information About Databases and Tables



​      What if you forget the name of a database or table, or what the      structure of a given table is (for example, what its columns are      called)? MySQL addresses this problem through several statements      that provide information about the databases and tables it      supports.    

​      You have previously seen [`SHOW       DATABASES`](sql-statements.md#show-databases), which lists the databases managed by the      server. To find out which database is currently selected, use the      [`DATABASE()`](functions.md#function_database) function:    

```
mysql> SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| menagerie  |
+------------+
```

​      If you have not yet selected any database, the result is      `NULL`.    

​      To find out what tables the default database contains (for      example, when you are not sure about the name of a table), use      this statement:    

```
mysql> SHOW TABLES;
+---------------------+
| Tables_in_menagerie |
+---------------------+
| eventf  |
| petf    |
+---------------------+
```

​      The name of the column in the output produced by this statement is      always      `Tables_in_*`db_name`*`,      where *`db_name`* is the name of the      database. See [Section 13.7.7.37, “SHOW TABLES Statement”](sql-statements.md#show-tables), for more information.    

​      If you want to find out about the structure of a table, the      [`DESCRIBE`](sql-statements.md#describe) statement is useful; it      displays information about each of a table's columns:    

```
mysql> DESCRIBE pet;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name    | varchar(20) | YES  |     | NULL    |       |
| owner   | varchar(20) | YES  |     | NULL    |       |
| species | varchar(20) | YES  |     | NULL    |       |
| sex     | char(1)     | YES  |     | NULL    |       |
| birth   | date        | YES  |     | NULL    |       |
| death   | date        | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
```

​      `Field` indicates the column name,      `Type` is the data type for the column,      `NULL` indicates whether the column can contain      `NULL` values, `Key` indicates      whether the column is indexed, and `Default`      specifies the column's default value. `Extra`      displays special information about columns: If a column was      created with the `AUTO_INCREMENT` option, the      value will be `auto_increment` rather than empty.    

​      `DESC` is a short form of      [`DESCRIBE`](sql-statements.md#describe). See      [Section 13.8.1, “DESCRIBE Statement”](sql-statements.md#describe), for more information.    

​      You can obtain the [`CREATE TABLE`](sql-statements.md#create-table)      statement necessary to create an existing table using the      [`SHOW CREATE TABLE`](sql-statements.md#show-create-table) statement. See      [Section 13.7.7.10, “SHOW CREATE TABLE Statement”](sql-statements.md#show-create-table).    

​      If you have indexes on a table, `SHOW INDEX FROM      *`tbl_name`*` produces information      about them. See [Section 13.7.7.22, “SHOW INDEX Statement”](sql-statements.md#show-index), for more about this      statement.

## 3.5 Using mysql in Batch Mode



​      In the previous sections, you used [**mysql**](programs.md#mysql)      interactively to enter statements and view the results. You can      also run [**mysql**](programs.md#mysql) in batch mode. To do this, put      the statements you want to run in a file, then tell      [**mysql**](programs.md#mysql) to read its input from the file:    

```
shell> mysql < batch-file
```

​      If you are running [**mysql**](programs.md#mysql) under Windows and have      some special characters in the file that cause problems, you can      do this:    

```
C:\> mysql -e "source batch-file"
```

​      If you need to specify connection parameters on the command line,      the command might look like this:    

```
shell> mysql -h host -u user -p < batch-file
Enter password: ********
```

​      When you use [**mysql**](programs.md#mysql) this way, you are creating a      script file, then executing the script.    

​      If you want the script to continue even if some of the statements      in it produce errors, you should use the      [`--force`](programs.md#option_mysql_force) command-line option.    

​      Why use a script? Here are a few reasons:

- ​ If you run a query repeatedly (say, every day or every week), making it a script enables you to avoid retyping it each time you execute it.        

- ​ You can generate new queries from existing ones that are similar by copying and editing script files.        

- ​ Batch mode can also be useful while you're developing a query, particularly for multiple-line statements or multiple-statement sequences. If you make a mistake, you don't have to retype everything. Just edit your script to correct the error, then tell [**mysql**](programs.md#mysql) to execute it again.        

- ​ If you have a query that produces a lot of output, you can run the output through a pager rather than watching it scroll off the top of your screen:        

  ```
  shell> mysql < batch-file | more
  ```

- ​ You can catch the output in a file for further processing:        

  ```
  shell> mysql < batch-file > mysql.out
  ```

- ​ You can distribute your script to other people so that they can also run the statements.        

- ​ Some situations do not allow for interactive use, for example, when you run a query from a **cron** job. In this case, you must use batch mode.

​      The default output format is different (more concise) when you run      [**mysql**](programs.md#mysql) in batch mode than when you use it      interactively. For example, the output of `SELECT DISTINCT      species FROM pet` looks like this when      [**mysql**](programs.md#mysql) is run interactively:    

```
+---------+
| species |
+---------+
| bird    |
| cat     |
| dog     |
| hamster |
| snake   |
+---------+
```

​      In batch mode, the output looks like this instead:    

```
species
bird
cat
dog
hamster
snake
```

​      If you want to get the interactive output format in batch mode,      use [**mysql -t**](programs.md#mysql). To echo to the output the      statements that are executed, use [**mysql -v**](programs.md#mysql).    



​      You can also use scripts from the [**mysql**](programs.md#mysql) prompt      by using the `source` command or      `\.` command:    

```
mysql> source filename;
mysql> \. filename
```

​      See [Section 4.5.1.5, “Executing SQL Statements from a Text File”](programs.md#mysql-batch-commands), for more information.

## 3.6 Examples of Common Queries

- [3.6.1 The Maximum Value for a Column](tutorial.md#example-maximum-column)
- [3.6.2 The Row Holding the Maximum of a Certain Column](tutorial.md#example-maximum-row)
- [3.6.3 Maximum of Column per Group](tutorial.md#example-maximum-column-group)
- [3.6.4 The Rows Holding the Group-wise Maximum of a Certain Column](tutorial.md#example-maximum-column-group-row)
- [3.6.5 Using User-Defined Variables](tutorial.md#example-user-variables)
- [3.6.6 Using Foreign Keys](tutorial.md#example-foreign-keys)
- [3.6.7 Searching on Two Keys](tutorial.md#searching-on-two-keys)
- [3.6.8 Calculating Visits Per Day](tutorial.md#calculating-days)
- [3.6.9 Using AUTO_INCREMENT](tutorial.md#example-auto-increment)



​      Here are examples of how to solve some common problems with MySQL.    

​      Some of the examples use the table `shop` to hold      the price of each article (item number) for certain traders      (dealers). Supposing that each trader has a single fixed price per      article, then (`article`,      `dealer`) is a primary key for the records.    

​      Start the command-line tool [**mysql**](programs.md#mysql) and select a      database:    

```
shell> mysql your-database-name
```

​      To create and populate the example table, use these statements:    

```
CREATE TABLE shop (
    article INT UNSIGNED  DEFAULT '0000' NOT NULL,
    dealer  CHAR(20)      DEFAULT ''     NOT NULL,
    price   DECIMAL(16,2) DEFAULT '0.00' NOT NULL,
    PRIMARY KEY(article, dealer));
INSERT INTO shop VALUES
    (1,'A',3.45),(1,'B',3.99),(2,'A',10.99),(3,'B',1.45),
    (3,'C',1.69),(3,'D',1.25),(4,'D',19.95);
```

​      After issuing the statements, the table should have the following      contents:    

```
SELECT * FROM shop ORDER BY article;

+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|       1 | A      |  3.45 |
|       1 | B      |  3.99 |
|       2 | A      | 10.99 |
|       3 | B      |  1.45 |
|       3 | C      |  1.69 |
|       3 | D      |  1.25 |
|       4 | D      | 19.95 |
+---------+--------+-------+
```

### 3.6.1 The Maximum Value for a Column

​        “What is the highest item number?”      

```
SELECT MAX(article) AS article FROM shop;

+---------+
| article |
+---------+
|       4 |
+---------+
```

### 3.6.2 The Row Holding the Maximum of a Certain Column

​        *Task: Find the number, dealer, and price of the most        expensive article.*      

​        This is easily done with a subquery:      

```
SELECT article, dealer, price
FROM   shop
WHERE  price=(SELECT MAX(price) FROM shop);

+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0004 | D      | 19.95 |
+---------+--------+-------+
```

​        Other solutions are to use a `LEFT JOIN` or to        sort all rows descending by price and get only the first row        using the MySQL-specific `LIMIT` clause:      

```
SELECT s1.article, s1.dealer, s1.price
FROM shop s1
LEFT JOIN shop s2 ON s1.price < s2.price
WHERE s2.article IS NULL;

SELECT article, dealer, price
FROM shop
ORDER BY price DESC
LIMIT 1;
```

Note

​ If there were several most expensive articles, each with a price of 19.95, the `LIMIT` solution would show only one of them.

### 3.6.3 Maximum of Column per Group

​        *Task: Find the highest price per article.*      

```
SELECT article, MAX(price) AS price
FROM   shop
GROUP BY article
ORDER BY article;

+---------+-------+
| article | price |
+---------+-------+
|    0001 |  3.99 |
|    0002 | 10.99 |
|    0003 |  1.69 |
|    0004 | 19.95 |
+---------+-------+
```

### 3.6.4 The Rows Holding the Group-wise Maximum of a Certain Column

​        *Task: For each article, find the dealer or dealers        with the most expensive price.*      

​        This problem can be solved with a subquery like this one:      

```
SELECT article, dealer, price
FROM   shop s1
WHERE  price=(SELECT MAX(s2.price)
f FROM shop s2
f WHERE s1.article = s2.article)
ORDER BY article;

+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0001 | B      |  3.99 |
|    0002 | A      | 10.99 |
|    0003 | C      |  1.69 |
|    0004 | D      | 19.95 |
+---------+--------+-------+
```

​        The preceding example uses a correlated subquery, which can be        inefficient (see [Section 13.2.11.7, “Correlated Subqueries”](sql-statements.md#correlated-subqueries)). Other        possibilities for solving the problem are to use an uncorrelated        subquery in the `FROM` clause, a `LEFT        JOIN`, or a common table expression with a window        function.      

​        Uncorrelated subquery:      

```
SELECT s1.article, dealer, s1.price
FROM shop s1
JOIN (
  SELECT article, MAX(price) AS price
  FROM shop
  GROUP BY article) AS s2
  ON s1.article = s2.article AND s1.price = s2.price
ORDER BY article;
```

​        `LEFT JOIN`:      

```
SELECT s1.article, s1.dealer, s1.price
FROM shop s1
LEFT JOIN shop s2 ON s1.article = s2.article AND s1.price < s2.price
WHERE s2.article IS NULL
ORDER BY s1.article;
```

​        The `LEFT JOIN` works on the basis that when        `s1.price` is at its maximum value, there is no        `s2.price` with a greater value and thus the        corresponding `s2.article` value is        `NULL`. See [Section 13.2.10.2, “JOIN Clause”](sql-statements.md#join).      

​        Common table expression with window function:      



```
WITH s1 AS (
   SELECT article, dealer, price,
 RANK() OVER (PARTITION BY article
f     ORDER BY price DESC
f         ) AS `Rank`
     FROM shop
)
SELECT article, dealer, price
  FROM s1
  WHERE `Rank` = 1
ORDER BY article;
```

### 3.6.5 Using User-Defined Variables

​        You can employ MySQL user variables to remember results without        having to store them in temporary variables in the client. (See        [Section 9.4, “User-Defined Variables”](language-structure.md#user-variables).)      

​        For example, to find the articles with the highest and lowest        price you can do this:      

```
mysql> SELECT @min_price:=MIN(price),@max_price:=MAX(price) FROM shop;
mysql> SELECT * FROM shop WHERE price=@min_price OR price=@max_price;
+---------+--------+-------+
| article | dealer | price |
+---------+--------+-------+
|    0003 | D      |  1.25 |
|    0004 | D      | 19.95 |
+---------+--------+-------+
```

Note

​ It is also possible to store the name of a database object such as a table or a column in a user variable and then to use this variable in an SQL statement; however, this requires the use of a prepared statement. See [Section 13.5, “Prepared Statements”](sql-statements.md#sql-prepared-statements), for more information.

### 3.6.6 Using Foreign Keys



​        In MySQL, `InnoDB` tables support checking of        foreign key constraints. See        [Chapter 15, *The InnoDB Storage Engine*](innodb-storage-engine.md), and        [Section 1.8.2.3, “FOREIGN KEY Constraint Differences”](introduction.md#ansi-diff-foreign-keys).      

​        A foreign key constraint is not required merely to join two        tables. For storage engines other than        `InnoDB`, it is possible when defining a column        to use a `REFERENCES        *`tbl_name`*(*`col_name`*)`        clause, which has no actual effect, and *serves only as        a memo or comment to you that the column which you are currently        defining is intended to refer to a column in another        table*. It is extremely important to realize when        using this syntax that:

- ​   MySQL does not perform any sort of check to make sure that   *`col_name`* actually exists in   *`tbl_name`* (or even that   *`tbl_name`* itself exists). 
- ​   MySQL does not perform any sort of action on   *`tbl_name`* such as deleting rows in   response to actions taken on rows in the table which you are   defining; in other words, this syntax induces no `ON   DELETE` or `ON UPDATE` behavior   whatsoever. (Although you can write an `ON   DELETE` or `ON UPDATE` clause as   part of the `REFERENCES` clause, it is also   ignored.) 
- ​   This syntax creates a *column*; it does   **not** create any sort of   index or key.

​        You can use a column so created as a join column, as shown here:      

```
CREATE TABLE person (
    id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    name CHAR(60) NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE shirt (
    id SMALLINT UNSIGNED NOT NULL AUTO_INCREMENT,
    style ENUM('t-shirt', 'polo', 'dress') NOT NULL,
    color ENUM('red', 'blue', 'orange', 'white', 'black') NOT NULL,
    owner SMALLINT UNSIGNED NOT NULL REFERENCES person(id),
    PRIMARY KEY (id)
);

INSERT INTO person VALUES (NULL, 'Antonio Paz');

SELECT @last := LAST_INSERT_ID();

INSERT INTO shirt VALUES
(NULL, 'polo', 'blue', @last),
(NULL, 'dress', 'white', @last),
(NULL, 't-shirt', 'blue', @last);

INSERT INTO person VALUES (NULL, 'Lilliana Angelovska');

SELECT @last := LAST_INSERT_ID();

INSERT INTO shirt VALUES
(NULL, 'dress', 'orange', @last),
(NULL, 'polo', 'red', @last),
(NULL, 'dress', 'blue', @last),
(NULL, 't-shirt', 'white', @last);

SELECT * FROM person;
+----+---------------------+
| id | namef   |
+----+---------------------+
|  1 | Antonio Paz         |
|  2 | Lilliana Angelovska |
+----+---------------------+

SELECT * FROM shirt;
+----+---------+--------+-------+
| id | style   | color  | owner |
+----+---------+--------+-------+
|  1 | polo    | blue   |     1 |
|  2 | dress   | white  |     1 |
|  3 | t-shirt | blue   |     1 |
|  4 | dress   | orange |     2 |
|  5 | polo    | red    |     2 |
|  6 | dress   | blue   |     2 |
|  7 | t-shirt | white  |     2 |
+----+---------+--------+-------+


SELECT s.* FROM person p INNER JOIN shirt s
   ON s.owner = p.id
 WHERE p.name LIKE 'Lilliana%'
   AND s.color <> 'white';

+----+-------+--------+-------+
| id | style | color  | owner |
+----+-------+--------+-------+
|  4 | dress | orange |     2 |
|  5 | polo  | red    |     2 |
|  6 | dress | blue   |     2 |
+----+-------+--------+-------+
```

​        When used in this fashion, the `REFERENCES`        clause is not displayed in the output of        [`SHOW CREATE TABLE`](sql-statements.md#show-create-table) or        [`DESCRIBE`](sql-statements.md#describe):      

```
SHOW CREATE TABLE shirt\G
*************************** 1. row ***************************
Table: shirt
Create Table: CREATE TABLE `shirt` (
`id` smallint(5) unsigned NOT NULL auto_increment,
`style` enum('t-shirt','polo','dress') NOT NULL,
`color` enum('red','blue','orange','white','black') NOT NULL,
`owner` smallint(5) unsigned NOT NULL,
PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8mb4
```

​        The use of `REFERENCES` in this way as a        comment or “reminder” in a column definition works        with `MyISAM` tables.

### 3.6.7 Searching on Two Keys



​        An [`OR`](functions.md#operator_or) using a single key is well        optimized, as is the handling of        [`AND`](functions.md#operator_and).      

​        The one tricky case is that of searching on two different keys        combined with [`OR`](functions.md#operator_or):      

```
SELECT field1_index, field2_index FROM test_table
WHERE field1_index = '1' OR  field2_index = '1'
```

​        This case is optimized. See        [Section 8.2.1.3, “Index Merge Optimization”](optimization.md#index-merge-optimization).      

​        You can also solve the problem efficiently by using a        [`UNION`](sql-statements.md#union) that combines the output of        two separate [`SELECT`](sql-statements.md#select) statements.        See [Section 13.2.10.3, “UNION Clause”](sql-statements.md#union).      

​        Each [`SELECT`](sql-statements.md#select) searches only one key        and can be optimized:      

```
SELECT field1_index, field2_index
    FROM test_table WHERE field1_index = '1'
UNION
SELECT field1_index, field2_index
    FROM test_table WHERE field2_index = '1';
```

### 3.6.8 Calculating Visits Per Day



​        The following example shows how you can use the bit group        functions to calculate the number of days per month a user has        visited a Web page.      

```
CREATE TABLE t1 (year YEAR, month INT UNSIGNED,
    day INT UNSIGNED);
INSERT INTO t1 VALUES(2000,1,1),(2000,1,20),(2000,1,30),(2000,2,2),
   (2000,2,23),(2000,2,23);
```

​        The example table contains year-month-day values representing        visits by users to the page. To determine how many different        days in each month these visits occur, use this query:      

```
SELECT year,month,BIT_COUNT(BIT_OR(1<<day)) AS days FROM t1
       GROUP BY year,month;
```

​        Which returns:      

```
+------+-------+------+
| year | month | days |
+------+-------+------+
| 2000 |     1 |    3 |
| 2000 |     2 |    2 |
+------+-------+------+
```

​        The query calculates how many different days appear in the table        for each year/month combination, with automatic removal of        duplicate entries.

### 3.6.9 Using AUTO_INCREMENT



​        The `AUTO_INCREMENT` attribute can be used to        generate a unique identity for new rows:      

```
CREATE TABLE animals (
     id MEDIUMINT NOT NULL AUTO_INCREMENT,
     name CHAR(30) NOT NULL,
     PRIMARY KEY (id)
);

INSERT INTO animals (name) VALUES
    ('dog'),('cat'),('penguin'),
    ('lax'),('whale'),('ostrich');

SELECT * FROM animals;
```

​        Which returns:      

```
+----+---------+
| id | name    |
+----+---------+
|  1 | dog     |
|  2 | cat     |
|  3 | penguin |
|  4 | lax     |
|  5 | whale   |
|  6 | ostrich |
+----+---------+
```

​        No value was specified for the `AUTO_INCREMENT`        column, so MySQL assigned sequence numbers automatically. You        can also explicitly assign 0 to the column to generate sequence        numbers, unless the        [`NO_AUTO_VALUE_ON_ZERO`](server-administration.md#sqlmode_no_auto_value_on_zero) SQL mode        is enabled. For example:      

```
INSERT INTO animals (id,name) VALUES(0,'groundhog');
```

​        If the column is declared `NOT NULL`, it is        also possible to assign `NULL` to the column to        generate sequence numbers. For example:      

```
INSERT INTO animals (id,name) VALUES(NULL,'squirrel');
```

​        When you insert any other value into an        `AUTO_INCREMENT` column, the column is set to        that value and the sequence is reset so that the next        automatically generated value follows sequentially from the        largest column value. For example:      

```
INSERT INTO animals (id,name) VALUES(100,'rabbit');
INSERT INTO animals (id,name) VALUES(NULL,'mouse');
SELECT * FROM animals;
+-----+-----------+
| id  | name      |
+-----+-----------+
|   1 | dog       |
|   2 | cat       |
|   3 | penguin   |
|   4 | lax       |
|   5 | whale     |
|   6 | ostrich   |
|   7 | groundhog |
|   8 | squirrel  |
| 100 | rabbit    |
| 101 | mouse     |
+-----+-----------+
```

​        Updating an existing `AUTO_INCREMENT` column        value also resets the `AUTO_INCREMENT`        sequence.      

​        You can retrieve the most recent automatically generated        `AUTO_INCREMENT` value with the        [`LAST_INSERT_ID()`](functions.md#function_last-insert-id) SQL function or        the [`mysql_insert_id()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-insert-id.html) C API        function. These functions are connection-specific, so their        return values are not affected by another connection which is        also performing inserts.      

​        Use the smallest integer data type for the        `AUTO_INCREMENT` column that is large enough to        hold the maximum sequence value you will need. When the column        reaches the upper limit of the data type, the next attempt to        generate a sequence number fails. Use the        `UNSIGNED` attribute if possible to allow a        greater range. For example, if you use        [`TINYINT`](data-types.md#integer-types), the maximum permissible        sequence number is 127. For        [`TINYINT         UNSIGNED`](data-types.md#integer-types), the maximum is 255. See        [Section 11.1.2, “Integer Types (Exact Value) - INTEGER, INT, SMALLINT, TINYINT,         MEDIUMINT, BIGINT”](data-types.md#integer-types) for the ranges of all the        integer types.

Note

​ For a multiple-row insert, [`LAST_INSERT_ID()`](functions.md#function_last-insert-id) and [`mysql_insert_id()`](https://dev.mysql.com/doc/c-api/8.0/en/mysql-insert-id.html) actually return the `AUTO_INCREMENT` key from the *first* of the inserted rows. This enables multiple-row inserts to be reproduced correctly on other servers in a replication setup.

​        To start with an `AUTO_INCREMENT` value other        than 1, set that value with [`CREATE         TABLE`](sql-statements.md#create-table) or [`ALTER TABLE`](sql-statements.md#alter-table),        like this:      

```
mysql> ALTER TABLE tbl AUTO_INCREMENT = 100;
```

#### InnoDB Notes

​ For information about `AUTO_INCREMENT` usage specific to `InnoDB`, see [Section 15.6.1.6, “AUTO_INCREMENT Handling in InnoDB”](innodb-storage-engine.md#innodb-auto-increment-handling).

#### MyISAM Notes

- ​f For `MyISAM` tables, you can specifyf `AUTO_INCREMENT` on a secondary column inf a multiple-column index. In this case, the generated valuef for the `AUTO_INCREMENT` column isf calculated asf [`MAX(*`auto_increment_column`*)f  + 1 WHEREf  prefix=*`given-prefix`*`](functions.md#function_max).f This is useful when you want to put data into orderedf groups.   

  ```
  CREATE TABLE animals (
      grp ENUM('fish','mammal','bird') NOT NULL,
      id MEDIUMINT NOT NULL AUTO_INCREMENT,
      name CHAR(30) NOT NULL,
      PRIMARY KEY (grp,id)
  ) ENGINE=MyISAM;
  
  INSERT INTO animals (grp,name) VALUES
      ('mammal','dog'),('mammal','cat'),
      ('bird','penguin'),('fish','lax'),('mammal','whale'),
      ('bird','ostrich');
  
  SELECT * FROM animals ORDER BY grp,id;
  ```

  ​f Which returns:   

  ```
  +--------+----+---------+
  | grp    | id | name    |
  +--------+----+---------+
  | fish   |  1 | lax     |
  | mammal |  1 | dog     |
  | mammal |  2 | cat     |
  | mammal |  3 | whale   |
  | bird   |  1 | penguin |
  | bird   |  2 | ostrich |
  +--------+----+---------+
  ```

  ​f In this case (when the `AUTO_INCREMENT`f column is part of a multiple-column index),f `AUTO_INCREMENT` values are reused if youf delete the row with the biggestf `AUTO_INCREMENT` value in any group. Thisf happens even for `MyISAM` tables, forf which `AUTO_INCREMENT` values normallyf are not reused.   

- ​f If the `AUTO_INCREMENT` column is part off multiple indexes, MySQL generates sequence values usingf the index that begins with thef `AUTO_INCREMENT` column, if there is one.f For example, if the `animals` tablef contained indexes `PRIMARY KEY (grp, id)`f and `INDEX (id)`, MySQL would ignore thef `PRIMARY KEY` for generating sequencef values. As a result, the table would contain a singlef sequence, not a sequence per `grp` value.

#### Further Reading

​ More information about `AUTO_INCREMENT` is available here:

- ​f How to assign the `AUTO_INCREMENT`f attribute to a column: [Section 13.1.20, “CREATE TABLE Statement”](sql-statements.md#create-table), andf [Section 13.1.9, “ALTER TABLE Statement”](sql-statements.md#alter-table).   
- ​f How `AUTO_INCREMENT` behaves depending onf thef [`NO_AUTO_VALUE_ON_ZERO`](server-administration.md#sqlmode_no_auto_value_on_zero)f SQL mode: [Section 5.1.11, “Server SQL Modes”](server-administration.md#sql-mode).   
- ​f How to use thef [`LAST_INSERT_ID()`](functions.md#function_last-insert-id) functionf to find the row that contains the most recentf `AUTO_INCREMENT` value:f [Section 12.15, “Information Functions”](functions.md#information-functions).   
- ​f Setting the `AUTO_INCREMENT` value to bef used: [Section 5.1.8, “Server System Variables”](server-administration.md#server-system-variables).   
- ​f [Section 15.6.1.6, “AUTO_INCREMENT Handling in InnoDB”](innodb-storage-engine.md#innodb-auto-increment-handling)   
- ​f `AUTO_INCREMENT` and replication:f [Section 17.5.1.1, “Replication and AUTO_INCREMENT”](replication.md#replication-features-auto-increment).   
- ​f Server-system variables related tof `AUTO_INCREMENT`f ([`auto_increment_increment`](replication.md#sysvar_auto_increment_increment)f andf [`auto_increment_offset`](replication.md#sysvar_auto_increment_offset))f that can be used for replication:f [Section 5.1.8, “Server System Variables”](server-administration.md#server-system-variables).

## 3.7 Using MySQL with Apache



​      There are programs that let you authenticate your users from a      MySQL database and also let you write your log files into a MySQL      table.    

​      You can change the Apache logging format to be easily readable by      MySQL by putting the following into the Apache configuration file:    

```
LogFormat \
        "\"%h\",%{%Y%m%d%H%M%S}t,%>s,\"%b\",\"%{Content-Type}o\",  \
        \"%U\",\"%{Referer}i\",\"%{User-Agent}i\""
```

​      To load a log file in that format into MySQL, you can use a      statement something like this:    

```
LOAD DATA INFILE '/local/access_log' INTO TABLE tbl_name
FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' ESCAPED BY '\\'
```

​      The named table should be created to have columns that correspond      to those that the `LogFormat` line writes to the      log file.