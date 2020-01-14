# [editor on GitHub](https://github.com/james-kingdom/james-kingdom.github.io/edit/master/index.md)

* 개인학습용도이고, 출처를 최대한 표기했으나 문제가 있다면 kingdomokay@gmail.com 연락 주세요. 

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
*  SparkContext - 스파크 클러스터에 접근하는 지점 SC변수
*  출처 -https://statkclee.github.io/bigdata/bigdata-pyspark-data-structure.html

*  from pyspark.sql import SparkSession
*  SparkSession - 파크 세션을 생성, spark.read.csv() 데이터 로드

*  sc.parallelize - 파이썬 리스트를 스파크 클러스터로 로드, RDD로 변환
*  sc.textFile    - 외부 텍스트 데이터를 스파크 클러스터로 로드, RDD로 변환
*  from pyspark.sql.types import *
*  spark.sql 정형데이터, StructType()으로 스키마 지정으로 속도향상, 
*  spark.read.csv('xxx.csv', header=True, schema=스키마StructType(), nullValue='NA')

*  Spark 데이터 추출 및 전처리, 출처 - https://wikidocs.net/16565

* 출처 블로그 
*  https://frhyme.github.io/python-lib/pyspark/ 설치 튜토리얼
*  https://wikidocs.net/16565           개념정리
*  https://jaeyung1001.tistory.com/59   함수정리

#  ECMAScript 6(ES6) - 
* 출처 https://jsdev.kr/t/es6/2944 
* http://woowabros.github.io/experience/2017/12/01/es6-experience.html
* https://velog.io/@godori/ES6-%EC%A0%95%EB%A6%AC-vpjmrh6hhe
* https://sanghaklee.tistory.com/54
* https://blog.asamaru.net/2017/08/14/top-10-es6-features/
* 기본 매개 변수 (Default Parameters)
* 템플릿 리터럴 (Template Literals)
* 멀티 라인 문자열 (Multi-line Strings)
* 비구조화 할당 (Destructuring Assignment)
* 향상된 객체 리터럴 (Enhanced Object Literals)
* 화살표 함수 (Arrow Functions)
* Promises
* 블록 범위 생성자 Let 및 Const (Block-Scoped Constructs Let and Const)
* 클래스 (Classes)
* 모듈 (Modules)

#  TypeScript 
* 자바스크립트 대체 언어의 하나로써 자바스크립트(ES5)의 Superset(상위확장)
#  CSS Paint API 
* 크롬 65에 추가됨, 프로그래밍 방식으로 이미지를 생성할 수 있기 때문에, 이미지를 참조하는 대신 paint 함수를 사용하여 <canvas> 요소와 유사하게 이미지를 그릴 수 있다
* paintWorklet - background에 속성 값으로 paint 함수를 사용하여 처리할 수 있다
* 출처 - https://wit.nts-corp.com/2018/05/02/5214
#  AtlasDB - 트랜잭션 분산 데이터베이스 MVCC (Multi-version Concurrency Control)구현, 다버전 병렬제어
* 출처 https://translate.google.com/translate?hl=ko&sl=en&u=https://conferences.oreilly.com/strata/stratany2013/public/schedule/detail/30923&prev=search

# Go Programming Language 
* Go는 2009년 구글이 개발한[2] 프로그래밍 언어이다. 가비지 컬렉션 기능이 있고, 병행성(concurrent)을 잘 지원하는 컴파일 언어다.
* 출처 - https://ko.wikipedia.org/wiki/Go_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4)

# 용어집=============================

*  MES (Manufacturing Execution System) - 생산관리시스템
*  출처 블로그 - https://m.blog.naver.com/computermate/220475304706
*  하둡 - 빅데이터 처리 프레임워크

* kubernetes 
*  서비스 디스커버리와 로드 밸런싱
*  스토리지 오케스트레이션
*  자동화된 롤아웃과 롤백
*  자동화된 빈 패킹(bin packing) 
*  자동화된 복구(self-healing) 
*  시크릿과 구성 관리
*  출처 - https://kubernetes.io/ko/docs/concepts/overview/what-is-kubernetes/

*  Amazon EMR - 분석도구
*  EMR Cluster - Scale up가능 node로 이루어짐, Master node, Core node, Task node - S3를 사용하는 컴퓨팅 노드, spot node 
*  Hadoop : EMR- Elastic MapReduce
*  Apache Hive : Apache Hadoop용 데이터 웨어하우스 시스템. Hive를 사용하면 데이터의 요약, 쿼리 및 분석을 수행(쿼리 언어인 HiveQL로 작성)
*  MapReduce : 맵리듀스(MapReduce)는 정보 검색을 위한 데이터 가공을 목적으로 개발된 분산 환경에서의 병렬 데이터 처리 기법이자 프로그래밍 모델
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

*  미시경제 : 개인이나 기업 등의 경제활동에 직접 영향을 미치는 것으로 구매와 관련한 개별상품가격, 취업관련 임금수준 등의 움직임에 대한 분야
*  거시경제 : 경기상황, 노동시장, 물가 등 국가경제의 움직임을 좌우하는 요소가 연구대상인 분야

*  PCA -> PPCA -> GPLVM -> GPDM 
*  PCA(Principal Component Analysis) : Linearity를 가정한 차원축소
*  PPCA : X의 mapping을 bayesian 입장에서 구한 것
*  GPLVM(Gaussian Process Latent Variable Models) : mapping이 nonlinear일 때로 일반화한 것
*  GPDM(Gaussian Process Dynamical models) : GPLVM의 time-series data 확장버전
*  출처 블로그 - https://ihwoo.tistory.com/84 출처 - http://valley.egloos.com/viewer/?url=http://hackos.egloos.com/157662

*  관련영상 
*  https://www.youtube.com/watch?v=RMPvnfn9-G4

* OLAP(On-Line Analytical Processing)은 데이터웨어하우스 활용 수단의 통칭인 BI(Business Intelligence)의 한 분야
* ETL - 데이터를 이관하는 과정 Extraction Transformation Load의 3가지 과정을 거치게 됩니다
* 출처: https://unabated.tistory.com/entry/DW-DM-OLAP의-이해 [랄라라]
* https://unabated.tistory.com/entry/DW-DM-OLAP%EC%9D%98-%EC%9D%B4%ED%95%B4

* kaggle - 전세계 데이터 과학자들이 자신이 만든 코드를 공유하고 경쟁하는 데이터 분석 플랫폼
* Kaggle Kernels - 데이터 과학 및 기계 학습을위한 클라우드 기반 워크 벤치
* 출처- https://blog.naver.com/pmw9440/221377363924, https://en.wikipedia.org/wiki/Kaggle



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


# Python==========
* PEP8 파이썬 코딩스타일 가이드
* 출처 - https://wayhome25.github.io/python/2017/05/04/pep8/
*   https://b.luavis.kr/python/python-convention

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
    
* 파이썬 언더스코어_ 
* 1. 인터프리터에서 사용되는 경우
* 2. 값을 무시하고 싶은 경우
* 3. 특별한 의미의 네이밍을 하는 경우
* 4. 국제화(i18n)/지역화(l10n) 함수로 사용되는 경우
* 5. 숫자 리터럴값의 자릿수 구분을 위한 구분자로써 사용할 때
* 출처 - https://mingrammer.com/underscore-in-python/

    
* 참고 블로그
*  https://wikidocs.net/4307 점프투 파이썬


# Pandas=========

*  import pandas as pd
  
*  csv_data = pd.read_csv('c:/dataset_file.csv',delimiter='\t')
*  csv_data

# Node.js=================
* 환경설치
* NPM - Node Package Manger (설치 https://nodejs.org/ko/download/)
* Nodejs설치시 NPM함께 설치됨
* 출처 - https://www.a-mean-blog.com/ko/blog/MEAN-Stack/%EA%B0%9C%EB%B0%9C-%ED%99%98%EA%B2%BD-%EA%B5%AC%EC%B6%95
* npm init ->package.json 파일 생성
* npm install -> dependency package 설치
* npm install --save body-parser  -> 웹브라우저의 form으로 전송된 data를 서버에서 쉽게 사용하기 위해
* npm install express --save -> node.js로 서버를 만드는 express프레임웍사용
* EJS  Embedded JavaScript - Express에서 dynamic website를 만들기 위해 template으로 사용되는 파일
* npm install --save ejs
* 텍스트에디터 Atom, VScode .. 
* Postman - REST API테스트 프로그램
* Node JS API 개발 - Node JS, Express프레임웍 활용 REST API
* HTTP Methods(HTTP Verbs) - GET, POST, PUT, PATCH, DELETE


#  커리어 (데이타 애널리스트/엔지니어/사이언티스트)===================
* 데이타 아날리스트 - 분석가
* 데이타 사이언티스트 - 분석결과를 알고리즘으로 변환
* 데이타 엔지니어 - 전처리개발, 알고리즘을 코딩으로 구현
* 1) 데이타 엔지니어가 데이타를 가져옴
* 2) 데이타 아날리스트가 분석
* 3) 데이터 사이언티스트가 그 데이타로 알고리즘을 만듦

* 인공지능 - 머신러닝, 딥러닝 알고리즘 이해
* 데이터마이닝 & 텍스트 analytic - 텍스트/자연어 처리 관련된 알고리즘
* 툴 활용도, R - 분석할때, 파이썬 - 인공지능 개발 구현


