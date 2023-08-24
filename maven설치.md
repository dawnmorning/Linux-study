## Maven 3.8.8 설치

0. 작업 디렉토리
   /root

1. 다운로드

```
wget --no-check-certificate https://dlcdn.apache.org/maven/maven-3/3.8.8/binaries/apache-maven-3.8.8-bin.tar.gz
```

2. 압축 풀기

```
tar xvfz apache-maven-3.8.8-bin.tar.gz
```

3. 설치

```
mv /root/apache-maven-3.8.8 /usr/local/poscodx2023/maven3.8

ln -s /usr/local/poscodx2023/maven3.8 /usr/local/poscodx2023/maven
```

4. 설정(/etc/profile)

```
# maven
export PATH=$PATH:/usr/local/poscodx2023/maven/bin
```

5. 확인
```
mvn --version
```
