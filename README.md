English | [中文](https://github.com/2293736867/ASmallSalaryManagementSystem/blob/master/README_ZH_cn.md)

# 1 What's this

A small salary management system with JavaFX and Spring Boot.

This repository includes：
- source code
- EXE and JAR packaged from front-end project 
- WAR and JAR packaged from back-end project

# 2 Run

## Back End Environment Required:
- OpenJDK 11+
- MySQL 8.0+
- Tomcat 9+(optional, not required for using JAR)

## Front End Environment Required:
- Mac/Linux: OpenJDK11+
- Windows: None

## 2.1 Back End
First, run backend JAR/WAR.

**Note: You need to start the database service firstly, and ensure that there is a database and correct user name and password.**

**You can import `resources/init.sql` directly.**
### JAR

```bash
7z x release/Backend/jar.7z
java -jar release/Backend/Backend.jar
```

### WAR

```bash
7z x release/Backend/war.7z
mv release/Backend/Backend.war TOMCAT_DIR/webapps/
TOCMAT_DIR/bin/startup.sh
```

## 2.2 Front End 

- Windows: Run exe directly
- Other system: Run JAR

```bash
7z x release/Frontend/jar.7z
java -jar release/Frontend/Frontend.jar
```

## 2.3 If run failed

If you fail to run it, you can open the project with IDEA to run directly in IDEA or package and run by yourself.

For convenience .gitignore file has been deleted generated by IDEA. And running front end project need to specify the module:

![](https://img-blog.csdnimg.cn/20200606171719997.png)

![](https://img-blog.csdnimg.cn/20200606171810118.png)

The backend project can be opened and run directly in IDEA. Also you need to ensure that the database service has been started and there is correct user name and password.

If project can not run directly, solution:

- 1. Create a new project, Maven project for the front end and Spring Boot project for the back end
- 2. Copy the source code and modify package
- 3. Copy dependency in `pom.xml` and import them
- 4. Copy resource files
- 5. Run

If none of the above methods work, please create a new issue or contact me(Email 2293736867@qq.com).

# 3 Admin Account

The default administrator account and password are:

```
admin
password
```

They can be modified in `application.properties`. It is recommended to encrypt them using `jasypt`.

# 4 Encryption

You can change `Jasypt Spring Boot Starter` in `pom.xml` to the latest version. And there is a test file. Write the plaintext in the `application.properties` then run the test and replace the original plaintext with cipertxt from console output.

# 5 Details 

[CSDN](https://blog.csdn.net/qq_27525611/article/details/105083135)

[博客园](https://www.cnblogs.com/6b7b5fc3/p/13054733.html)

[Github Pages](https://www.bingling.site/post/javafxspringbootyan-zheng-ma-gong-neng-de-xiao-xing-xin-chou-guan-li-xi-tong/)


# Update log
# 06/29/2020
Update `README.md`.

# 06/15/2020

Update the description of the HTTPS and the verification code of the blog. By default there is lacking of HTTPS and the verification code function. If you need HTTPS, please modify them:

- `com.test.network.OKHTTP`
- `resources/key/pem.pem`

The backend needs to be deployed also. See the blog for details.

If you need the SMS function and use Tencent cloud API, you can modify `application.properties` directly. Using other API please modify them:

- Front End:

- `com.test.network.OKHTTP`
- `com.test.network.request.SendSmsRequest`
- `com.test.network.requestBuilder.SendSmsRequestBuilder`
- `com.test.controller.start.RetrievePasswordController`

- Back End:
- `com.test.controller.SmsController`

# 06/11/2020
Fix a CORS problem:

![](https://s1.ax1x.com/2020/06/11/tqZ6JO.png)

It was occurred when debugging with Postwoman sending a GET/POST request. `@CrossOrigin` annotation was added on the controller to fix this problem. If using other port please modify port value in `@CrossOrigin` by yourself.

# 06/10/2020

Fix `Field injection is not recommended`:

![](https://img-blog.csdnimg.cn/20200610210255455.png)

[References](https://blog.csdn.net/jianzhang11/article/details/105283642)

Using `@RequiredArgsConstructor` instead of using `@Autowired` directly.




