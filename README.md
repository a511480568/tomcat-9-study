## Welcome to Apache Tomcat!

### 编译过程
1. JDK：17
2. 添加pom文件
3. 在根目录下创建 home 文件夹，，将根目录下的 conf 文件复制到 home 文件夹下，将根目录下的 webapps 文件夹复制到 home 文件夹下，只留下 ROOT 文件夹，其余删除
4. 创建启动 Application，添加启动类：org.apache.catalina.startup.Bootstrap，并添加 VM options:
    ```markdown
    -Dcatalina.home=/Volumes/mymac/project/java/tomcat-main/home
    -Dcatalina.base=/Volumes/mymac/project/java/tomcat-main/home
    -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager
    -Djava.util.logging.config.file=/Volumes/mymac/project/java/tomcat-main/home/conf/logging.properties
    -Dfile.encoding=utf-8
   ```
5. 在 **org.apache.catalina.startup.ContextConfig#configureStart** 方法中添加:context.addServletContainerInitializer(new JasperInitializer(), null); 这是为了启动后能正常返回index.jsp 文件
6. 如果出现乱码到话，在 org.apache.tomcat.util.res.StringManager#getString(String key) 方法最后添加如下代码:
    ```java
        if (str != null) {
            str = new String(str.getBytes(StandardCharsets.ISO_8859_1),
                    StandardCharsets.UTF_8);
        }
    ```
7. 运行，浏览器访问 http://localhost:8080/

### What Is It?

The Apache Tomcat® software is an open source implementation of the Java
Servlet, JavaServer Pages, Java Expression Language and Java WebSocket
technologies. The Java Servlet, JavaServer Pages, Java Expression Language and
Java WebSocket specifications are developed under the
[Java Community Process](https://jcp.org/en/introduction/overview).

The Apache Tomcat software is developed in an open and participatory
environment and released under the
[Apache License version 2](https://www.apache.org/licenses/). The Apache Tomcat
project is intended to be a collaboration of the best-of-breed developers from
around the world. We invite you to participate in this open development
project. To learn more about getting involved,
[click here](https://tomcat.apache.org/getinvolved.html) or keep reading.

Apache Tomcat software powers numerous large-scale, mission-critical web
applications across a diverse range of industries and organizations. Some of
these users and their stories are listed on the
[PoweredBy wiki page](https://wiki.apache.org/tomcat/PoweredBy).

Apache Tomcat, Tomcat, Apache, the Apache feather, and the Apache Tomcat
project logo are trademarks of the Apache Software Foundation.

### Get It

For every major Tomcat version there is one download page containing
links to the latest binary and source code downloads, but also
links for browsing the download directories and archives:
- [Tomcat 10](https://tomcat.apache.org/download-10.cgi)
- [Tomcat 9](https://tomcat.apache.org/download-90.cgi)
- [Tomcat 8](https://tomcat.apache.org/download-80.cgi)
- [Tomcat 7](https://tomcat.apache.org/download-70.cgi)

To facilitate choosing the right major Tomcat version one, we have provided a
[version overview page](https://tomcat.apache.org/whichversion.html).

### Documentation

The documentation available as of the date of this release is
included in the docs webapp which ships with tomcat. You can access that webapp
by starting tomcat and visiting <http://localhost:8080/docs/> in your browser.
The most up-to-date documentation for each version can be found at:
- [Tomcat 10](https://tomcat.apache.org/tomcat-10.1-doc/)
- [Tomcat 9](https://tomcat.apache.org/tomcat-9.0-doc/)
- [Tomcat 8](https://tomcat.apache.org/tomcat-8.5-doc/)
- [Tomcat 7](https://tomcat.apache.org/tomcat-7.0-doc/)

### Installation

Please see [RUNNING.txt](RUNNING.txt) for more info.

### Licensing

Please see [LICENSE](LICENSE) for more info.

### Support and Mailing List Information

* Free community support is available through the
[tomcat-users](https://tomcat.apache.org/lists.html#tomcat-users) email list and
a dedicated [IRC channel](https://tomcat.apache.org/irc.html) (#tomcat on
Freenode).

* If you want freely available support for running Apache Tomcat, please see the
resources page [here](https://tomcat.apache.org/findhelp.html).

* If you want to be informed about new code releases, bug fixes,
security fixes, general news and information about Apache Tomcat, please
subscribe to the
[tomcat-announce](https://tomcat.apache.org/lists.html#tomcat-announce) email
list.

* If you have a concrete bug report for Apache Tomcat, please see the
instructions for reporting a bug
[here](https://tomcat.apache.org/bugreport.html).

### Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for more info.
