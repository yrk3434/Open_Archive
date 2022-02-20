- anaconda prompt에서 pyspark 치고 다음 명령 실행해도 되고 주피터 노트북에서 pyspark 라이브러리 임포트해서 사용해도 됨


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

- groupBy 연산
- R의 group_by(col)%>%summarise(...) 연산과 비슷
```
 dutchpay.groupBy("category_col").count().show() # 카테고리 별 개수 세기
 dutchpay.groupBy("category_col").sum('amount').show() # 카테고리 별 amount 컬럼의 값의 합 구하기
```
