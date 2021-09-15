#ORM(Object-Relational Mapping)

-------------------------------------

##ORM이란?
ORM은 객체와 관계형 데이터베이스를 연결해 주는 것을 의미한다.
데이터베이스의 테이블을 객체와 연결하여 테이블에 CRUD를 할 때 SQL쿼리를 사용하지 않고 가능하게 만들어 준다.
<br><br>
##CREATE

CREATE TABLE

---------------------

modles.py에서 클래스로 테이블을 구성하고 makemigrations, migrate를 해준다
* SQL
~~~
CREATE TABLE `user` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(50) NOT NULL,
  'password' VARCHAR(50) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY ('username')
)
~~~
* ORM
~~~
class User(models.Model):
    username = models.CharField(max_length=50, unique=True)
    password = models.CharField(max_length=50)
~~~
<br><br>
INSERT

------------------------------
* SQL
~~~
INSERT INTO user(id, username, password) VALUES (1, '갱', '12345');
~~~
* ORM
~~~
new_user = User.objects.create(username='user1', password='12345')
~~~
~~~
new_user = User(username='user1', password='12345')
new_user.save
~~~

<br><br>

##READ
ALL
* SQL
~~~
SELECT * FROM user;
~~~
* ORM
~~~
User.objects.all()
~~~
<br>

WHERE
* SQL
~~~
SELECT * FROM user WHERE id=1;
~~~
* ORM
~~~
User.objects.filter(id=1)
~~~
<br><br>
##UPDATE
* SQL
~~~
UPDATE user SET password = '12345' WHERE id=1;
~~~

* ORM
~~~
user = User.objects.get(id=1)
user.password = '12345'
user.save()
~~~
<br><br>

##DELETE
* SQL
~~~
DELETE FROM user WHERE id=1;
~~~

* ORM
~~~
User.objects.get(id=1)
~~~
<br><br>

## 값 가져오기
* SQL
~~~
SELECT now_floor FROM now WHERE u_id=20;
~~~

* ORM
~~~
now = Now.objects.all()
now = now.objects.get(u_id=20)
~~~


