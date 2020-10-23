site: https://sites.google.com/site/beigesoftware

Beigesoft™ Enterprise Information System final standard WEB application (WAR, included Beigesoft Web-Store with PayPal payment method).

It's WEB interface based on standard JEE MVC servlet, JSP, JSTL.
It's based on previous beigesoft-webcrud and weboio projects.
Default configuration is PostgreSQL (web.xml) and context.xml for Tomcat JEE JDBC authentication. For MySql rename web-mysql.xml and context-mysql.xml respectively.

Tested/works OK on last Java8 (and last Android 29), Tomcat 7.0.82/8.5.43, Maven 3.5.2, Ant 1.10.6, PostgreSQL 9.6.12, MySQL 5.5.5-10.1.38-MariaDB
Fixed Tomcat 8.5.43, error: ...An invalid character [44] was present in the Cookie value... COMMA
!Maven 3.6.1 gives error findbugs (but not yet checked for spotbugs)!

To install application on Apache Tomcat 7/8:
1. you should have MySql server with created user and empty database
2. make sure that Tomcat has libraries: HikariCP-2.4.3.jar, postgresql-9.4-1206-jdbc4.jar (or mysql-connector-java-5.1.40.jar), slf4j-api-1.7.12.jar (versions may be different)
3. Unpack WAR file and change user/password/database with yours ones in WEB-INF/classes/potrgres(or mysql)/cmnst.xml:
...
<entry key="dbUrl">[yourdb]</entry>
<entry key="dbUsr">[yourdbusername]</entry>
<entry key="dbPsw">[yourdbuserpass]</entry>
...
or MySql:
...
<entry key="dbUrl">jdbc:mysql://localhost/[yourdb]</entry>
<entry key="checkTbl">select * from INFORMATION_SCHEMA.TABLES where TABLE_SCHEMA='[yourdb]' and TABLE_NAME=':tblNm';</entry>
...

change security roles in web.xml

  Pack new WAR file (it is actually ZIP archive).
4. copy WAR file inside "[tomcat_home]/webapps"
5. type in browser address same as WAR file i.e. "https://[server-address]/beige-accweb"
6. after creating database add users with SQL query:
insert into USTMC (USR, PWD, VER) values ('[useradmin]', '[strongpassword]', 1);
insert into USTMC (USR, PWD, VER) values ('[useruser]', '[strongpassword]', 1);
insert into USRLTMC (USR, ROL, VER)  values ('[useradmin]', '[role1]', 1);
insert into USRLTMC (USR, ROL, VER)  values ('[useruser]', '[role2]', 1);

This is "cloud" version i.e. it's available through network (WEB), so you must make sure that it's used reliable encrypted (HTTPS) connection.

license:
BSD 2-Clause License
https://sites.google.com/site/beigesoftware/bsd2csl


3-D PARTY LICENSES:

Apache Standard Taglib Implementation (JSTL):
The Apache Software License, Version 2.0
http://www.apache.org/licenses/LICENSE-2.0.txt

PayPal SDK License
https://github.com/paypal/PayPal-Java-SDK/blob/master/LICENSE.txt

JavaMail API (compat) 1.4 plus JavaBeans(TM) Activation Framework:
Common Development and Distribution License (CDDL) v1.0
https://glassfish.dev.java.net/public/CDDLv1.0.html

CSS/Javascript framework Bootstrap by Twitter, Inc and the Bootstrap Authors:
MIT License
https://github.com/twbs/bootstrap/blob/master/LICENSE

JQuery by JS Foundation and other contributors:
MIT license
https://jquery.org/license

JS library Popper by Federico Zivolo and contributors:
MIT License
https://github.com/twbs/bootstrap/blob/master/LICENSE

Open Iconic icon fonts by Waybury:
SIL OPEN FONT LICENSE Version 1.1
http://scripts.sil.org/cms/scripts/page.php?item_id=OFL_web
Open Iconic to Bootstrap CSS by Waybury:
MIT License
https://github.com/twbs/bootstrap/blob/master/LICENSE

DejaVu fonts by Bitstream:
https://dejavu-fonts.github.io/License.html

flag-icon-css collection of all country flags in SVG by Panayiotis Lipiridis
MIT License
https://github.com/lipis/flag-icon-css


