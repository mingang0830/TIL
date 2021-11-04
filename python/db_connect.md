# 파이썬 SQlite3 연결하기

----------------------------------------

## 파이썬 SQLite3 라이브러리 불러오기
~~~
import sqlite3
~~~

## DB 연결, 커서 획득
~~~
conn = sqlite3.connect("test.db")

# 커서 획득
c = conn.cursor()
~~~
파이썬에서 파일을 읽고 쓰려면 커서를 가져와야 함.

## SQL문 실행
~~~
c.execute("SQL QUERY")
~~~

## 데이터 불러오기
~~~
c.execute("SELECT * FROM table1").fetchone() # 한 줄만 가져오기
c.execute("SELECT * FROM table1").fetchall() # 전체 가져오기
~~~

## DB 커밋과 연결 해제
~~~
conn.commit()
conn.close()
~~~

