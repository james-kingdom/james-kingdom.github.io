# [editor on GitHub](https://github.com/james-kingdom/james-kingdom.github.io/edit/master/index.md)

# 용어집==================
*  하둡 - 빅데이터 처리 프레임워크
*  Amazon EMR - 분석도구
*  EMR Cluster - Scale up가능 node로 이루어짐, Master node, Core node, Task node - S3를 사용하는 컴퓨팅 노드, spot node 
*  Hadoop : EMR- Elastic MapReduce
*  AWS S3 - simple storage service 
*  pyspark - spark API 
*  스파크 RDD(Resilient Distributed Datase), 코어, SQL, Mlib, GraphX
*  Glue for ETL - Spark&Hive interface in web browser : 서버 없이 ETL도구
*  ElasticSearch - 분석도구
*  Kibana - 데쉬보드
*  Amazon Kinesis -실시간 분석도구
*  Amazon Redshift : Data warehouse 
*  Managed service 
*  빅데이터 수집 S/W - Flume, Sqoop:RDBS와 HDFS로 Bulk 가져오는, R, Python 
*  빅데이터 저장 S/W - HDFS, HBASE : 컬럼기반 NoSQL
*  빅데이터 처리 S/W - 맵리듀스:병렬처리, 피그, 하이브, 스파크:인메모리방식, 우지 R, 파이썬 : 판다스, 넘파이, 싸이파이,,,
*  빅데이터 분석 S/W - 스파크, R, 파이썬
*  빅데이터 시각화 S/W - 엑셀, 스프레드시트, 차트, 퓨전테이블, 타블로우, 클릭뷰, R: ggplot

*  관련영상 
*  https://www.youtube.com/watch?v=RMPvnfn9-G4

# Map Reduce
* 개념 - 정보 검색을 위한 데이터 가공(색인어 추출, 정렬 및 역 인덱스 생성)을 목적으로 개발된 분산 환경에서의 병렬 데이터 처리 기법이자 프로그래밍 모델이다

* 참고블로그
* https://m.blog.naver.com/PostView.nhn?blogId=jevida&logNo=140199795866&proxyReferer=https%3A%2F%2Fwww.google.com%2F

# Data Modeling=====
* ERD (Entity Relation-ship Diagram) 개념->논리->물리->구현->운영DB
* 데이터 모델링 - 업무 프로세스를 추상화 하여 데이터베이스의 데이터로 표현하는 설계
* 아키텍처관점 1) 요구사항분석 2) 개념모델링 3) 논리모델링 
* 구체화 관점 4) 물리 모델링 5) 데이터베이스
* 데이터관점 - Entity Type, 프로세스관점 - SQL, 데이터프로세스 - Relation-ship, 상관관점 - CRUD

* 참고 블로그 
* http://blog.skby.net/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-data-modeling/

# Apache Spark=====

* pyspark설치
*  java_home classpath설치
*  conda install pyspark 
*  pyspark 

* 분석라이브러리들
*  import time
*  import matplotlib.pyplot as plt
*  import numpy as np 
*  import pandas as pd
*  from pyspark import SparkContext

* 참고 블로그 
*  https://frhyme.github.io/python-lib/pyspark/ 설치 튜토리얼
*  https://wikidocs.net/16565           개념정리
*  https://jaeyung1001.tistory.com/59   함수정리

# Python==========
* 사용자입력
* number = input("숫자를 입력하세요: ")

* 자료형
* 리스트 
*  리스트명 = [요소1, 요소2, 요소3, ...]

* 튜플 
*  튜플명 = (요소1, 요소2, 요소3, ...)
*  리스트는 그 값의 생성, 삭제, 수정이 가능하지만 튜플은 그 값을 바꿀 수 없다
*  괄호( )를 생략해도 무방

* 딕셔너리
*  dic = {Key1:Value1, Key2:Value2, Key3:Value3, ...}
*  딕셔너리에서 Key는 고유한 값이므로 중복되는 Key 값을 설정해 놓으면 하나를 제외한 나머지 것들이 모두 무시

* 집합자료형
*  집합명 = set([1,2,3,4])
*  중복을 허용하지 않는다.순서가 없다(Unordered).

* 함수
*  def 함수명(인자):
*    내용
*    return result
* 클래스
*  class 클래스명:
*    def __init__(self, first, second): # 생성자, self:생성되는 객체
*    #def setdata(self, first, second):
*        self.first = first
*        self.second = second
*    def 함수명(인자):
*        내용
*        return result
    
* 참고 블로그
*  https://wikidocs.net/4307 점프투 파이썬


# Pandas=========

*  import pandas as pd
  
*  csv_data = pd.read_csv('c:/dataset_file.csv',delimiter='\t')
*  csv_data
