git 2.9.5 설치

1. 의존성 라이브러리

```
yum -y install curl-devel
yum -y install expat-devel
yum -y install gettext-devel
yum -y install openssl-devel
yum -y install zlib-devel
yum -y install perl-devel

```

2. 다운로드

```
wget --no-check-certificate https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz

```

3. 압축 풀기

```
tar xvfz git-2.9.5.tar.gz
```

4.소스 디렉토리

```
cd git-2.9.5
```

# pwd

5. configure

```
./configure --prefix=/usr/local/poscodx2023/git
```

6. 빌드

```
make all
```

7. 설치

```
make install
```

8. 설정(/etc/profile)

# git

```
export PATH=$PATH:/usr/local/poscodx2023/git/bin
```

```
git --version
```

9. git 사용하기

```
mkdir my-workspace

cd my-workspace

git clone https://github.com/dawnmorning/java-study.git

```

10. old version 처리
```
whereis git
/usr/bin/git /usr/share/man/man1/git.1.gz

mv /usr/bin/git /usr/bin/git.ol
ln -s /usr/local/poscodx2023/git/bin/git /usr/bin/git
git --version
```
