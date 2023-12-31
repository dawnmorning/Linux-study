0. 작업 디렉토리

# pwd

# /root

1. 의존 라이브러리 설치

```
# yum install -y gcc
# yum install -y gcc-c++
# yum install -y libtermcap-devel
# yum install -y gdbm-devel
# yum install -y zlib*
# yum install -y libxml*
# yum install -y freetype*
# yum install -y libpng*
# yum install -y flex
# yum install -y gmp
# yum install -y ncurses-devel
# yum install -y cmake.x86_64
# yum install -y libaio

iconv 소스 컴파일 설치를 한다.

# wget --no-check-certificate https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.17.tar.gz
# tar xvfz libiconv-1.17.tar.gz
# cd libiconv-1.17.tar.gz
# ./configure --prefix=/usr/local
# make
# make install
```

2. 소스 다운로드

```
# wget --no-check-certificate https://downloads.mariadb.org/interstitial/mariadb-10.1.48/source/mariadb-10.1.48.tar.gz
```

3. 압축 풀기

```
# tar xvfz mariadb-10.1.48.tar.gz
```

4. 소스 이동

```
# cd mariadb-10.1.48
```

5. 빌드 환경 설정

```
# cmake -DCMAKE_INSTALL_PREFIX=/usr/local/poscodx2023/mariadb -DMYSQL_USER=mysql -DMYSQL_TCP_PORT=3307 -DMYSQL_DATADIR=/usr/local/poscodx2023/mariadb/data -DMYSQL_UNIX_ADDR=/usr/local/poscodx2023/mariadb/tmp/mariadb.sock -DINSTALL_SYSCONFDIR=/usr/local/poscodx2023/mariadb/etc -DINSTALL_SYSCONF2DIR=/usr/local/poscodx2023/mariadb/etc/my.cnf.d -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DWITH_EXTRA_CHARSETS=all -DWITH_ARIA_STORAGE_ENGINE=1 -DWITH_XTRADB_STORAGE_ENGINE=1 -DWITH_ARCHIVE_STORAGE_ENGINE=1 -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_PARTITION_STORAGE_ENGINE=1 -DWITH_BLACKHOLE_STORAGE_ENGINE=1 -DWITH_FEDERATEDX_STORAGE_ENGINE=1 -DWITH_PERFSCHEMA_STORAGE_ENGINE=1 -DWITH_READLINE=1 -DWITH_SSL=bundled -DWITH_ZLIB=system
```

6. 빌드

```
# make
```

7. 설치

```
# make install


# cd (작업은 /root)

# pwd

# /root
```

8. 계정 생성

```
# groupadd mysql

# useradd -M -g mysql mysql
```

9. 인스톨 디렉토리 /mariadb 소유자 변경

```
# chown -R mysql:mysql /usr/local/poscodx2023/mariadb
```

10. 설정파일 위치 변경

```
    cp -R /usr/local/poscodx2023/mariadb/etc/my.cnf.d /etc
```

11. 기본(관리) 데이터베이스(mysql) 생성

```
# /usr/local/poscodx2023/mariadb/scripts/mysql_install_db --user=mysql --basedir=/usr/local/poscodx2023/mariadb --defaults-file=/usr/local/poscodx2023/mariadb/etc/my.cnf --datadir=/usr/local/poscodx2023/mariadb/data
```

12. 서버 구동

```
# /usr/local/poscodx2023/mariadb/bin/mysqld_safe &
```

13. root 패스워드 설정

```
# /usr/local/poscodx2023/mariadb/bin/mysqladmin -u root password '비밀번호'
```

14. 데이터베이스 접속 테스트

```
# /usr/local/poscodx2023/mariadb/bin/mysql -u root -p
```

15. path 설정(/etc/profile)

```
vi /etc/profile
# mariadb

export PATH=$PATH:/usr/local/poscodx2023/mariadb/bin
-----
source /etc/profile

mysql

mysql -u root -p
```

16. 서비스(데몬, Daemon) 등록/시작/중지

```
# cp /usr/local/poscodx2023/mariadb/support-files/mysql.server /etc/init.d/mariadb

# chkconfig mariadb on (centos7이상: systemctl enable mariadb)

# ps -ef | grep mysqld

# kill -9 6031 5959

# ps -ef | grep mysqld

# systemctl start mariadb

# mysql -u root (-D mysql) -p

# exit

# reboot

centos 부터 재부팅
```
