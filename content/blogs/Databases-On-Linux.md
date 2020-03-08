+++ 
date = "2013-08-27"
title = "Databases On Linux"
tags = []
categories = ["technical"]

+++
**Database Management Systems**

Database software can be generally organized into three categories: SQL, Xbase, and desktop databases. _SQL-based databases_ are professional-level relational databases whose files are managed by a central database server program. Applications that use the database do not access the files directly. Instead, they send requests to the database server, which then performs the actual access. _SQL_ is the query language used on these industrial strength databases. Both are open source projects freely available for your use. The _Xbase language_ is an enhanced version of the dBase programming language used to access database files whose formats were originally developed for dBase on the PC. With Xbase, DBMSs can directly access the database files. Xbase is used mainly for smaller personal databases, with database files often located on a user’s own system.

Linux has proved itself capable of supporting complex and demanding database management tasks. In addition, many free SQL databases are available for Linux that offer much the same functionality. Most commercial databases also provide free personal versions, as do Oracle, Adabas D, and MySQL.

**PostgreSQL**

 PostgreSQL is based on the POSTGRES DBMS, though it uses SQL as its query language. POSTGRES is a next-generation research prototype developed at the University of California, Berkeley. Linux versions of PostgreSQL are included in most distributions. You can find more information on it from the [PostgreSQL website](www.postgresql.org). PostgreSQL is an open source project, developed under the GPL license.

**MySQL**

 MySQL is a true multiuser, multithreaded SQL database server, supported by MySQL AB. MySQL is an open source product available free under the GPL license. You can obtain current information on it from its [website](www.mysql.com). The site includes detailed documentation, including manuals and FAQs.

**Oracle**

Oracle offers a fully functional version of its Oracle9i DBMS for Linux, as well as the Oracle Application Server. You can download trial versions from the [Oracle website](www.oracle.com). Oracle is a professional DBMS for large databases specifically designed for Internet e-business tasks. The Oracle Application Server provides support for real-time and commerce applications on the Web. As Linux is a fully functional version of UNIX, Oracle is particularly effective on it.

Oracle was originally designed to operate on UNIX, and Linux is a far better platform for it than other PC operating systems. Oracle offers extensive documentation for its Linux version that you can download from its documentation page, to which you can link from the Support pages on its website.

The documentation available includes an installation guide, an administrator’s reference, and release notes, as well as the generic documentation. You can find specific information on installing and configuring Oracle for Linux in the Oracle Database HOWTO. 
  
![Oracle on Linux](/images/oracle-linux.jpg)

**Informix**

Informix (now controlled by IBM) offers an integrated platform of Internet-based applications called Informix Internet Foundation.2000 on Linux. These include the Informix Dynamic Server, their database server. Informix Dynamic Server features Dynamic Scalable Architecture, making it capable of effectively using any hardware setup. Informix provides only commercial products. No free versions exist, though the company currently provides special promotions for Linux products. You can find out more about Informix at[www-4.ibm.com/software/data/informix](www-4.ibm.com/software/data/informix) . Informix strongly supports Linux development of its Informix line. You can find out more about Informix for Linux at [www-306.ibm.com/software/data/informix/linux](www-306.ibm.com/software/data/informix/linux).

**Sybase**

For Linux, Sybase offers the Sybase Adaptive Server Enterprise server (see [www.sybase.com](www.sybase.com)). You can currently download the Adaptive Server Enterprise server from the website. The Sybase Enterprise database features data integration that coordinates all information resources on a network. SQL Anywhere is a database system designed for smaller databases, though with the same level of complexity found in larger databases.

**DB2**

IBM provides a Linux version of its DB2 Universal Database software. You can download it free from the IBM DB2 web page for Linux,[www.software.ibm.com/data/db2/linux](www.software.ibm.com/data/db2/linux). DB2 Universal Database for Linux includes Internet functionality along with support for Java and Perl. With the Web Control Center, administrators can maintain databases from a web browser. DB2 features scalability to expand the database easily, support for Binary Large Objects, and cost based optimization for fast access. DB2 is still very much a mainframe database, though IBM is currently working on refining its Unix/Linux version.

**MaxDB**

MaxDB is a SAP-certified database, originally developed by SAP. It provides capabilities comparable to many of the professional-level databases. MaxDB is now developed by the MySQL AB project, mysql.com. Recently, the MySQL AB project also added MAX DB, formerly SAP DB.

**GNU SQL**

GNU SQL is the GNU relational database developed by a group at the Institute for System Programming of the Russian Academy of Sciences and supported by the GNU organization. It is a portable multiuser DBMS with a client/server structure that supports SQL. The server processes requests and performs basic administrative operations, such as unloading parts of the database used infrequently. The clients can reside on any computer of a local network.

GNU SQL uses a dialect of SQL based on the SQL-89 standard and is designed for use on a Unix-like environment. You can download the database software from the GNU FTP site at [ftp.gnu.org](ftp.gnu.org). For more information, contact the GNU SQL website at [ispras.ru/~kml/gss](ispras.ru/~kml/gss).

**Xbase Databases**

Databases accessed with Xbase are smaller in scale, designed for small networks or for personal use. Many are originally PC database programs, such as dBase III, Clipper, FoxPro, and Quicksilver. Currently, only Flagship provides an interface for accessing Xbase database files.

**NoSQL Database**

A NoSQL database provides a mechanism for storage and retrieval of data that uses looser [consistency models](https://en.wikipedia.org/wiki/Consistency_model) than traditional [relational databases](https://en.wikipedia.org/wiki/Relational_database). Motivations for this approach include simplicity of design, [horizontal scaling](https://en.wikipedia.org/wiki/Scalability#Horizontal_and_vertical_scaling) and finer control over availability. NoSQL databases are often highly optimized [key–value stores](https://en.wikipedia.org/wiki/NoSQL#Key.E2.80.93value_stores) intended for simple retrieval and appending operations, with the goal being significant performance benefits in terms of [latency](https://en.wikipedia.org/wiki/Latency) and [throughput](https://en.wikipedia.org/wiki/Throughput). NoSQL databases are finding significant and growing industry use in [big data](https://en.wikipedia.org/wiki/Big_data) and [real-time](https://en.wikipedia.org/wiki/Real-time_web) web applications. NoSQL systems are also referred to as “Not only SQL” to emphasize that they do in fact allow SQL-like query languages to be used. More information can be found on [http://nosql-database.org/](http://nosql-database.org/).

__Flagship__ is a compiler with which you can create interfaces for querying Xbase database files. The interfaces support menus and dialog boxes, and they have function calls that execute certain database queries. Flagship can compile dBase III+ code and up. It is compatible with dBase and Clipper, and can access most Xbase file formats, such as __.dbf, .dbt, .fmt,__ and __.frm__. One of Flagship’s key features is that its interfaces can be attached to a web page, enabling users to update databases. Flagship is commercial software, though you can download a free personal version from its website at [fship.com/free.html](fship.com/free.html).

