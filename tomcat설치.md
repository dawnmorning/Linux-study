0. 작업은 /root

1. tomcat8 다운로드

```
wget --no-check-certificate https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.79/bin/apache-tomcat-9.0.79.tar.gz
```

2. 압축 풀기

```
tar xvfz apache-tomcat-9.0.79.tar.gz
```

3. 설치

```
mv apache-tomcat-9.0.79 /usr/local/poscodx2023/tomcat9.0

ln -s /usr/local/poscodx2023/tomcat9.0 /usr/local/poscodx2023/tomcat
```

4. 설정(/etc/profile, 생략)

5. 포트 확인

```
vi /usr/local/poscodx2023/tomcat/conf/server.xml

8080 open 확인
```

6. 실행

```
/usr/local/poscodx2023/tomcat/bin/catalina.sh start

ps -ef | grep tomcat
```

7. 브라우저로 접근 하기

```
http://설치서버:8080
```

8. 중지 시키기

```
/usr/local/poscodx2023/tomcat/bin/catalina.sh stop
```

9. 서비스 등록 하기

```
/usr/lib/systemd/system/tomcat.service 파일 생성

systemctl enable tomcat
```

10. tomcat 서비스 실행/중지/재실행

```
systemctl start tomcat

systemctl stop tomcat

systemctl restart tomcat
```

11. tomcat manager 설정

```
1)  tomcat-users.xml 설정
vi /usr/local/poscodx2023/tomcat/conf/tomcat-users.xml
```

========================================================

```
<tomcat-users>
. . .
. . .
<role rolename="manager"/>
<role rolename="manager-gui" />
<role rolename="manager-script" />
<role rolename="manager-jmx" />
<role rolename="manager-status" />
<role rolename="admin"/>
<user username="admin" password="manager" roles="admin,manager,manager-gui, manager-script, manager-jmx, manager-status"/>
</tomcat-users>


```

/usr/local/poscodx2023/tomcat/webapps/manager/META-INF/context.xml
주석 처리
<Context>
....
</Context>

새로 다음내용 추가
<Context antiResourceLocking="false" privileged="true" docBase="${catalina.home}/webapps/manager">
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="^.*$" />
</Context>

```




========================================================

12. tomcat 재시작

    # systemctl stop tomcat

    # ps -ef | grep tomcat

    # systemctl start tomcat

13. http://본인 ip주소/manager
```
