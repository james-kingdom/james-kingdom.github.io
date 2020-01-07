# [editor on GitHub](https://github.com/james-kingdom/james-kingdom.github.io/edit/master/index.md)

# Palantir Gotham Titan==================
* 참조사이트 - https://translate.google.com/translate?hl=ko&sl=en&u=https://www.palantir.com/about/&prev=search
*  Conjure - HTTP / JSON API 용 오픈 소스 툴체인 
   (YAML로 작성된 선언적 API 정의에서 다양한 언어로 클라이언트 및 서버 바인딩을 생성)
* YAML - Yaml An't Markup Language
* 개체탐색기는 Horizon으로 구동됨
* Palantir Horizon -  Palantir Gotham's Horizon in-memory database (Apache Spark과 유사)
* Palantir Ava - Palantir Gotham 생태계에 적용된 인공 지능 기능 모음
* Palantir Dossier - Intelligence Products 사용자는 협업하여 분석을 공유하고 보고서를 작성하며 실시간으로 지능을 발견 할 수 있습니다.
* Palantir Gaia - Map 응용 프로그램은 실시간으로 공유되는 실시간Map를 제공하여 모든 사람이 동일한 정보에 대해 행동 할 수 있도록 실시간으로 지상에서 일어나는 상황을 추적합니다
* Nexus Peering 모듈 - 전 세계의 데이터를 동기화하여 원격 지역의 성능을 향상 시키면서도 안전한 협업과 일관된 데이터 액세스를 계속할 수 있습니다

# 용어집==================
*  MES (Manufacturing Execution System) - 생산관리시스템
*  참조 블로그 - https://m.blog.naver.com/computermate/220475304706
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

*  미시경제 : 개인이나 기업 등의 경제활동에 직접 영향을 미치는 것으로 구매와 관련한 개별상품가격, 취업관련 임금수준 등의 움직임에 대한 분야
*  거시경제 : 경기상황, 노동시장, 물가 등 국가경제의 움직임을 좌우하는 요소가 연구대상인 분야

*  PCA -> PPCA -> GPLVM -> GPDM 
*  PCA(Principal Component Analysis) : Linearity를 가정한 차원축소
*  PPCA : X의 mapping을 bayesian 입장에서 구한 것
*  GPLVM(Gaussian Process Latent Variable Models) : mapping이 nonlinear일 때로 일반화한 것
*  GPDM(Gaussian Process Dynamical models) : GPLVM의 time-series data 확장버전
*  관련 블로그 - https://ihwoo.tistory.com/84 출처 - http://valley.egloos.com/viewer/?url=http://hackos.egloos.com/157662

*  관련영상 
*  https://www.youtube.com/watch?v=RMPvnfn9-G4

*  ECMAScript 6(ES6) - 
*  참조블로그 https://jsdev.kr/t/es6/2944 
*  http://woowabros.github.io/experience/2017/12/01/es6-experience.html
*  https://velog.io/@godori/ES6-%EC%A0%95%EB%A6%AC-vpjmrh6hhe
*  https://sanghaklee.tistory.com/54
*  https://blog.asamaru.net/2017/08/14/top-10-es6-features/
*  기본 매개 변수 (Default Parameters)
*  템플릿 리터럴 (Template Literals)
*  멀티 라인 문자열 (Multi-line Strings)
*  비구조화 할당 (Destructuring Assignment)
*  향상된 객체 리터럴 (Enhanced Object Literals)
*  화살표 함수 (Arrow Functions)
*  Promises
*  블록 범위 생성자 Let 및 Const (Block-Scoped Constructs Let and Const)
*  클래스 (Classes)
*  모듈 (Modules)


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
