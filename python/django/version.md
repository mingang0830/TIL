## EC2에서 버전 맞추기

--------------------------------------------------
만들어둔 게시판앱의 파이썬 버전이 3.8.10 인데 ec2에 설치되어 있는 파이썬은 3.7 버전이어서 버전을 맞춰줘야함

버전 확인
~~~
$ python3 --version
Python 3.7.10
~~~

미리 설치해둬야 할것
~~~
$ sudo yum update 
$ sudo yum upgrade
$ sudo yum install gcc openssl-devel bzip2-devel libffi-devel
~~~

파이썬 원하는 버전 다운, 압축 해제, 해당 폴더로 이동
~~~
$ sudo wget https://www.python.org/ftp/python/3.8.10/Python-3.8.10.tgz
$ sudo tar zxf Python-3.8.10.tgz
$ cd Python-3.8.10/
~~~

컴파일
~~~
$ sudo ./configure --prefix=/opt/python3
$ sudo make install
~~~

기존에 있는거 이름 변경하고 링크해서 사용하기
~~~
$ sudo mv /usr/bin/python3 /usr/bin/_python3
$ sudo ln -s /opt/python3/bin/python3 /usr/bin/python3
~~~

설정 완료!
~~~
$ python3 --version
Python 3.8.10
~~~
