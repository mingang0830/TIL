## 파이썬 업그레이드 후 yum 실행 오류

------------------------------------------------

파이썬을 3.8.10 으로 업그레이드 한 후 생긴 yum 에러
~~~
$ yum update

   File "/usr/bin/yum", line 30
     except KeyboardInterrupt, e:
                             ^
 SyntaxError: invalid syntax
~~~
  
이유는 yum은 기본적으로 python2.7을 사용하는데 버전 업그레이드를 하면서 syntaxError 가 발생  
yum 스크립트를 수정해줘야 함    
  
스크립트 확인
~~~
$ cat /usr/bin/yum

!/usr/bin/python
~~~

스크립트 수정
~~~
$ sudo vi /usr/bin/yum

#!/usr/bin/python2

$ sudo vi /usr/libexec/urlgrabber-ext-down

#!/usr/bin/python2
~~~    

정상적으로 동작! 
