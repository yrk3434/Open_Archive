R의 dplyr 사용법과 매우 유사함

- 데이터 생성
```
from pyspark.sql import SparkSession
spark = SparkSession.builder.getOrCreate()

myList = [('1','a',1.4),('2','b',2.5),('4','c',3.2)]
df = spark.createDataFrame(myList)
```

- 데이터 불러오기 및 조회

```
data = spark.read.csv("데이터경로\\파일명.csv", header="true", inferSchema="true")
data.show() # head 기능, 데이터 조회
data.show(2) # 2개의 행 조회

data.printSchema() # 컬럼 타입(string, double 등) 확인
```

- 칼럼단위 연산은 기본적으로 select를 이용해서!
```
data.select('column1') # 특정 열의 데이터 추출 -> 확인하려면 data.select('column1').show()
```

- 기존 행을 이용해 새로운 행 만들기 (R의 mutate와 유사)

```
data.selct(
```
