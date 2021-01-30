# [editor on GitHub](https://github.com/james-kingdom/james-kingdom.github.io/edit/master/index.md)

# 쿠버네티스 실습
* https://itguava.tistory.com/124

# AWS 
* 윈도우 CLI설치 https://s3.amazonaws.com/aws-cli/AWSCLI64.msi 다운로드
* 리눅스 CLI설치 curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

# eclipe 에서 pyspark 개발환경
* 출처 - https://enahwe.wordpress.com/2015/11/25/how-to-configure-eclipse-for-developing-with-python-and-spark-on-hadoop/
* eclipse 모듈설치 PyDev - http://pydev.org/updates 추가하여 설치 후 
* Preferences"창에서 : PyDev> Interpreters> Python Interpreter 에서 상단 python.exe설치경로 추가

# hive 
* 출처 -  https://m.blog.naver.com/PostView.nhn?blogId=airguy76&logNo=150189416769&proxyReferer=https:%2F%2Fwww.google.com%2F
* conf/hive-site.xml 생성하여 metastore (mysql) 정보 지정, lib에 mysql connector .jar 파일 넣기  hdfs, mysql 서버켜고, bin/hive로 구동 show tables;
* hive-site.xml에 default.fs.name ->hdfs://localhost:9000  중요, 
* external 테이블 생성 hive> CREATE EXTERNAL TABLE fct_data( fc_date string, location string) PARTITIONED BY (part_date string, part_location STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t' STORED AS TEXTFILE;
* 메타스토어 (mysql/mariadb)스키마생성 hive --service schemaTool -dbType mysql -initSchema 
* 이때 timezone 에러시 mariadb.conf/mysql.conf에서 default-time-zone='+9:00' 추가 후mysql 재가동 후 스키마 재생성

# oracle 접속 pyspark 파티션 조정옵션
* var df = spark.read.format("iris").option("dbtable","SELECT * FROM mytable")
*                   .option("partitionColumn", "columnA")
*                   .option("lowerBound", 0)
*                   .option("upperBound", 10000)
*                   .option("numPartitions", 2)
*                   .load()

# mysql
* vim /etc/mysql/mysql.conf.d/mysqld.cnf 에서 포트랑 타임존 등 확인 수정
* sudo apt-get install mysql-server
* sudo service mysql stop
* sudo usermod -d /var/lib/mysql/ mysql
* sudo /usr/bin/mysqld_safe --skip-grant-tables
* mysql -u root mysql
* mysql과 mariadb 중복설치 후 꼬였을때 완전삭제방법
* [Mysql]
* sudo apt-get purge mysql-server
* sudo apt-get purge mysql-common
* [MariaDB]
* sudo apt-get purge mariadb-server
* sudo apt-get purge mariadb-common
* [공용작업]
* sudo rm -rf /var/log/mysql
* sudo rm -rf /var/log/mysql.*
* sudo rm -rf /var/lib/mysql
* sudo rm -rf /etc/mysql

* wsl 우분투 재시작 -> powershell에서 Restart-Service LxssManager
* 리눅스 profile수정 오류시 vi나 ls 등 명령어 안될때 export PATH=/usr/bin:/bin
* 리눅스 apt-get install 등 안될때 sudo rm -rf /etc/apt/apt.conf.d/20snapd.conf 삭제 후 시도
* 리눅스 크론탭 ***** 분.시.일.월.몇요일: 0 ~ 6(0 = 일요일, 1 = 월요일)
* 리눅스 크론탭 #1분 마다 스크립트 실행 * * * * * /usr/bin/backup.sh >> /var/log/backup.log
* 리눅스 크론탭 10분 마다 스크립트 실행 */10 * * * * /usr/backup.sh >> /var/log/backup.log

# airflow 
* 출처 - https://bcho.tistory.com/1184
* 출처 - https://m.blog.naver.com/PostView.nhn?blogId=occidere&logNo=221773113221&proxyReferer=https:%2F%2Fwww.google.com%2F
* windows wsl 환경 설정 후 sudo apt install python3  & sudo apt install python-pip python-pip3 그리고 pip3 install apache-airflow
* etc/profile 에 export AIRFLOW_HOME= 홈설정 후 airflow db init 
* 유저추가 airflow user create -r Admin -u bread -e bread@bread.com -f bread -l sung -p 123456677753 
* 다시한번 airflow db init  후 airflow webserver -p 8888 
* 사용법 > 
* 1) airflow dags list 목록 확인 후 
* 2) dags 폴더에서 vim my_first.py 생성 후 파이선실행 python3 my_first 
* 3) airflow tasks list my_first_dag 
* 4) task 실행 airflow tasks test my_first_dag print_date 2019-06-01T09:00:00
* 5) 스케쥴 등록 airflow scheduler 후에 웹서버 airflow webserver -p 8888 실행 후 웹접속 dags 확인
* 6-1) dag = DAG(dag_id='dagid명', default_args=datatime(년월일시분초), schedule_interval="@once")
* 6-2) t1 .... t2 = BashOperator(task_id='타스크명',bash_command='echo "실행할 명령어"',dag=dag 6-1dag명시) t1 >> t2 순서정의

# Apache atlas 소개
* 출처 - http://www.kwangsiklee.com/2018/05/apache-atlas%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80/

# 람다아키텍처 이해
* 출처 : https://blog.naver.com/phh0606c/222180224300
* 1. 람다 아키텍처 개요 
* 2. ingetion : Kafka, RabbitMQ 
* 3. fileformat : Avro , Parquet
* 5. Data Processing : Batch / Streaming
* 4. fileSystem : HDFS - 왜 HDFS을 쓸까? 
* 6. Batch Processing : MapReduce/Spark 
* 7. Streaming Processing : Spark Streaming / Storm 
* 8. DataBase 1 : Hbase 
* 9. Cluster Management Tool
* 10. Workflow Monitoring Tools : hue

# Spark master slave 클러스터 모드로 실행
* sbin> start-master.sh 실행, start-slave -m 128M spark://bread9@bread9-vm.mshome.net:7077 실행
* bin> pyspark --master spark://bread9@bread9-vm.mshome.net:7077 실행 하여 확인
* 모니터링 http://bread9-vm.mshome.net:8080/ 
* spark-env.sh 추가 export SPARK_WORKER_INSTANCES=3
* 출처 https://jdm.kr/blog/167

* 그외 spark기본설정사항 출처 https://glow153.tistory.com/16
*  conf/spark-env.sh
(... 파일 내용 하단에 추가)
* export SPARK_WORKER_INSTANCES = 8
* export SPARK_WORKER_CORES = 1
* export SPARK_WORKER_MEMORY = 128
* export JAVA_HOME=/home/user/apps/java
* export HADOOP_HOME=/home/witlab/apps/hadoop
* export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
* export LD_LIBRARY_PATH=$HADOOP_HOME/lib/native
* export SPARK_LOCAL_IP="xxx.xxx.xxx.xxx"  # your local ip
* export PYSPARK_PYTHON=/usr/bin/python3
* export PYSPARK_DRIVER_PYTHON=/usr/bin/python3
* export SPARK_MASTER_HOST=localhost

* conf/spark-defaults.conf
* spark.master                     spark://localhost:7077
*   2.2.2 spark 성능 향상 (선택사항, 절대적인 설정이 아님!) (참고 : link)
* spark.executor.instances=1
* spark.executor.cores=3
* spark.executor.memory=4g
* spark.driver.cores=1
* spark.driver.memory=4g

# 리눅스 캐시메모리 삭제
* sync && echo 3 > /proc/sys/vm/drop_caches https://blog.lael.be/post/1090

# 리눅스 파티션 프로그램 설치
* sudo apt-get install gparted   https://miiingo.tistory.com/221

# 윈도우에 설치하기 용 
#	Zookeeper
*	출처 : https://man-tae.tistory.com/3
*	다운로드 : http://www.apache.org/dyn/closer.cgi/zookeeper/
*	설정파일수정: 압축해제후 zookeeper-3.4.14\conf 경로에 있는 zoo_sample.cfg 복사하여 zoo.cfg생성 후 dataDir=data로변경
*	실행방법 : zkServer.cmd 실행

#	kafka설치
*	다운로드 : https://kafka.apache.org/downloads
*	설정파일수정: config\server.properties수정  log.dirs=\kafka_2.11-1.1.0\logs
*	실행방법
*1) 주키퍼실행 apache-zookeeper-3.5.8\bin/zkServer.cmd
*2) 카프카실행 kafka_2.13-2.6.0\bin\windows\kafka-server-start.bat config\server.properties
*3) 카프카예제 토픽생성 kafka_2.13-2.6.0\bin\windows\kafka-topics.bat –create –zookeeper localhost:2181 –replication-factor 1 –partitions 1 –topic test20190715
*4) 카프카예제 리스트조회 kafka_2.13-2.6.0\bin\windows\kafka-topics.bat –list –zookeeper localhost:2181
*5) 카프카예제 컨슈머시작 kafka_2.13-2.6.0\bin\windows\kafka-console-consumer.bat –bootstrap-server localhost:9092 –topic test20190715

#	hadoop-2.7.1 
* 하둡 safemode 조치명령어 sudo -u hdfs hdfs dfsadmin -safemode leave
*	출처: https://icodebroker.tistory.com/4218 [ICODEBROKER]
*	다운로드 : https://archive.apache.org/dist/hadoop/core/hadoop-2.6.0/
*	설정파일수정 (첨부 hadoop-2.7.1설정.zi 참고)
*1) hdfs환경설정 : hadoop-env.cmd, hdfs-site.xml, core-site.xml, slaves
*2) yarn환경설정 : mapred-site.xml, yarn-site.xml
*3) 환경 변수 초기화 하기
*hadoop-2.6.0\etc\hadoop\hadoop-env.cmd실행
*4) 파일 시스템 포맷하기
*hdfs namenode -format 명령어 실행
*5) HDFS 데몬 시작하기
*hadoop-2.6.0\sbin\start-dfs.cmd 실행
*hadoop-2.6.0\sbin\start-yarn.cmd 실행
*6) 서비스 확인 
* JPS실행 및 http://localhost:8088 http://localhost:50070
* 맵리듀스 예제확인 첨부 자바파일 

#	Zeppelin을 다운로드 (all-interpreters버전 1.5기가)
* 다운로드 : https://zeppelin.apache.org/download.html 
* 실행방법 : 사전에 Hadoop_home이 설정 된 상태에서 D:\ADT\zeppelin-0.9.0-preview2-bin-all\bin\zeppelin.cmd실행
* 이슈 : Web application not found D:\ADT\zeppelin-0.9.0-preview2-bin-all\bin\zeppelin-web-angular\dist
* 조치 : D:\ADT\zeppelin-0.9.0-preview2-bin-all\zeppelin-web-angular-0.9.0-preview2.war를 위 경로에 압축해제 후 가동

#	PostgreSQL
* Tutorial&download : https://www.enterprisedb.com/postgres-tutorials/connecting-postgresql-using-psql-and-pgadmin

#	Pentaho Data Integration 
* 개요 : https://hhgg.tistory.com/2
* 다운로드 : https://sourceforge.net/projects/pentaho/
* Tutorial : https://www.hitachivantara.com/en-us/products/data-management-analytics/pentaho/tutorials.html?ecid=ms_glo_bd_en_sscepen02?icid=as_us_en_2020068
* 윈도우 커멘드 JOB 실행 Pan.bat /file:D:\ADT\pentaho\trans1.ktr /level:basic
* spon.bat - transformation 및 job을 작성, 편집, 실행하거나 디버깅할 때 사용
* pan.bat - Spoon에서 생성한 transformation을 커맨드라인에서 독립적으로 실행할 때 사용
* kitchen.bat - Spoon에서 설계한 job을 커맨드라인에서 독립적으로 실행할 때 사용
* carte.bat - 전용 원격 ETL서버를 설정할 수 있는 경량의 웹 컨테이너
* Pentaho 서버의 수동 설치를위한 Linux 환경을 https://help.pentaho.com/Documentation/9.0/Setup/Prepare_your_Linux_environment_for_a_manual_installation
* Carte.bat localhost 8883 실행후   
* http://localhost:8883/kettle/executeTrans/?trans=D:\ADT\pentaho\workspace\s3-maria_filter_select_groupby.ktr 이런식으로 URL접근하면 실행되고
* http://localhost:8883/kettle/status/ 에서 Transformation 이름상세 보기


#	Talend Open Studio
* 다운로드 : https://www.talend.com/download/thankyou/data-integration-windows/?file=TOS_DI-Win32-20200219_1130-V7.3.1.exe
* Tutorial : https://www.talend.com/resources/filtering-data-using-tmap-component/
# hadoop 설치중 (윈도우) 
* 윈도우에 hdfs 설치 https://icodebroker.tistory.com/4218
* hdfs테스트 (https://kamang-it.tistory.com/entry/Hadoop-03%EB%A7%B5%EB%A6%AC%EB%93%80%EC%8A%A4-%EC%98%88%EC%A0%9CWordCount?category=707479?category=707479)
* http://localhost:8088/cluster/nodes/unhealthy  http://localhost:50070/dfshealth.html#tab-overview

# kafka 
* Kafka 용어 정리(출처 - https://man-tae.tistory.com/12?category=800764)
* windows 환경에서 zookeeper 설치 및 실행(출처 - https://man-tae.tistory.com/3)
* windows 환경에서 kafka 설치 및 실행 (출처 - https://man-tae.tistory.com/5?category=800764)
* 1) 주키퍼실행 apache-zookeeper-3.5.8\bin/zkServer.cmd
* 2) 카프카실행 kafka_2.13-2.6.0\bin\windows\kafka-server-start.bat config\server.properties 
* 3) 카프카예제 토픽생성  kafka_2.13-2.6.0\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test20190715
* 4) 카프카예제 리스트조회 kafka_2.13-2.6.0\bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
* 5) 카프카예제 컨슈머시작 kafka_2.13-2.6.0\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic test20190715

# pentaho data integration
* tutorial
https://www.hitachivantara.com/en-us/products/data-management-analytics/pentaho/tutorials.html?ecid=ms_glo_bd_en_sscepen02?icid=as_us_en_2020068#getting-started

# talend open studio
* tutorial
https://www.talend.com/resources/filtering-data-using-tmap-component/

# Gradle
Groovy를 기반으로 한 오픈소스 빌드 도구이다. Ant의 자유도와 Maven의 관례를 통한 접근성을 바탕으로 이전 빌드툴의 단점을 보완하여 개선된 서비스를 제공한다
(출처 https://ko.wikipedia.org/wiki/Gradle)

# 데이터사이언스
* 출처 - https://blog.naver.com/dsz08082/222034174003
1) 시계열 분석
* 목표 - 1. 미래값예측, 2) 데이터특성파악
* 정상성 개념 - 미래는 확률적으로 과거와 동일하다는 의미로 시작된 시계열 분석의 특징
* 정상성을 만족하는 시계열은 1) 평균값은 시간에 관계없이 일정, 2) 분산값은 시간에 관계없이 일정 3) 공분산은 시간에 의존하지 않고 오직 시차에만 의존함(주기가 일정하다)
* 자기상관 : 시점 t와 t-1간 상관관계
* 시계열 모형 
* 자기회귀모형( AR, AutoRegressive), 이동평균모형(MA), 자기회귀누적 이동모형(ARMIA), 분해
* 분해 시계열 : 시계열에 영향을 주는 일반요인을 시계열에서 분리해 분석하는 방법 (추세, 계절, 순환, 불규칙 등 요인들)
2) 상관 분석
* 상관계수(r) : 두변수간 관련성,  (피어슨/스피어만/켄달의순위 상관계수 방법) 대표적으로 피어슨만 상관계수 방법론 ( 등간척도, 비율척도)
* 계수는 1에 가까울수록 상관정도가 높고 0에 접근하면 낮다 
* 상관분석 절차
 ㄱ. 산점도를 그려 두 변수의 대략적인 관계 파악
 ㄴ. 상관계수에 필요한 통계량 산정
 ㄷ. 상관계수 산정
 ㄹ. 모상고나계수에 대한 유의성검정
 ㅁ. 결정계수 산정
 ㅂ. 상관계수와 결정계수 제시 및 상관 분석 결과 설명
* 공분산 : 두 확률변수가 얼마나 같이 변하는지 측정
* 그외 다차원 척도법 : 유사성 및 비 유사성을 측정해 2차원 또는 3차원 공간상에 표현하는 분석 방법
3) 회귀분석
* 회귀분석 : 변수간 관계를 알아보는 통계적 분석 방법 (목적 : 독립변수에 의하여 종석변수값을 예측)
- 독립변수 : 종속변수에 영향을 미치는 변수, 종속변수 : 분석의 대상이 되는 변수
* 선형회귀모형 : 독립변수x, y의 확률분포 관계가 1차식일경우, 독립변수 개수에 따른 단순회귀분석/ 다중회귀분석 
* 회귀모형 설정값인 설명변수 선택은 ㄱ)모든가능한조합, 2)단계적변수선택 법등이 있음
* 정규화선형회귀(릿지회귀, 라소회귀, 엘라스틱넷 회귀)
* 앙상블, 랜덤포레스트 참고 : https://joyfuls.tistory.com/62
4) 데이터마이닝
* 정의 : 유용한 정보를 찾는 과정
* 데이터마이닝 대표 6가지 기능 
* 1) 분류(classification) : 분류기법다양, 의사결정나무, 랜덤포레스트 등
* 2) 추정(estimation) : 연속된 변수 값 추정에 사용, 신경망 모형 등
* 3) 예측(prediction) : 입력 데이터 성격에 따라 의사결정나무, 신경망 예측등
* 4) 연관분석(association analysis) : 장바구니 분석 과같이 아이템의연관성을 파악하는 분석
* 5) 군집(clustering) : 분류와 달리 다른레코드와의 유사성에 의해 그룹화 되고 이질성의 의해 세분화, 데이터마이닝이나 모델링의 준비단계로 사용
* 6) 기술(description) : 데이터 분석 의미 단순 기술
https://blog.naver.com/chgchi76/221349463581
1) 연관(association) : 지지도, 신뢰도, 향상도, apriori알고리즘
2) 시간(sequence): 시계열성, lstm, 언어모델링/분석
3) 분류(classification) : decision tree 
4) 군집(clustering) : k-means알고리즘, k-medoids, nearest neighbor, 계층적군집화, som 차원축소
5) 특징(characterization) : PCA

* 데이터마이닝 5단계 : 1. 목적정의 2. 데이터준비 3. 데이터가공 4. 데이터마이닝 기법 적용 5. 검증
https://blog.naver.com/dsz08082/222048119542

# H2o AutoML 
*아래는 h2o 가이드.
* https://docs.h2o.ai/h2o/latest-stable/h2o-docs/starting-h2o.html#id1
*아래는 h2o 머신러닝으로 암 (양성 or 악성)판별한건데 흥미롭네요.
* https://partrita.github.io/posts/H2O/

# h2o auto-ml rstudio
* https://niceguy1575.tistory.com/entry/%F0%9F%92%A6-R-%EA%B8%B0%EB%B0%98-H2O-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%B6%84%EC%84%9D%EC%BD%94%EB%93%9C-Setup-Processing?category=738019
# 의사결정트리
* https://niceguy1575.tistory.com/entry/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%A7%88%EC%9D%B4%EB%8B%9D-9-Decision-TREE-%EC%9D%98%EC%82%AC%EA%B2%B0%EC%A0%95%EB%82%98%EB%AC%B4%EC%99%80-%EB%82%98%EB%AC%B4%EC%9D%98-%ED%9B%84%EC%98%88%EB%93%A4Bagging-Random-forest-Boosting?category=738019
* https://datascienceschool.net/view-notebook/16c28c8c192147bfb3d4059474209e0a/

* 개인학습용도이고, 출처를 최대한 표기했으나 문제가 있다면 kingdomokay@gmail.com 연락 주세요. 
# hadoop 설치중 (리눅스)
* https://ssup2.github.io/record/Hadoop_%EC%84%A4%EC%B9%98_%EC%84%A4%EC%A0%95_Ubuntu_18.04/
# hadoop Permission denied (publickey,password).
* ssh-keygen -t rsa -P '' -f /root/.ssh/id_rsa
* cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
* chmod og-wx /root/.ssh/authorized_keys
* vi $HADOOP_HOME/etc/hadoop/hadoop-env.sh
* export HDFS_NAMENODE_USER=root
* export HDFS_DATANODE_USER=root
* export HDFS_SECONDARYNAMENODE_USER=root
* export YARN_RESOURCEMANAGER_USER=root
* export YARN_NODEMANAGER_USER=root

# SSH 서버 설정 접속
* sudo apt-get update
* sudo apt-get install openssh-server
* sudo apt-get install ssh
* sudo bash install.sh
* sudo service ssh start

# zookeeper 설치
* https://eyeballs.tistory.com/107?category=740961

# ambari-server설치 (ubuntu 18)
* wget -O /etc/apt/sources.list.d/ambari.list http://public-repo-1.hortonworks.com/ambari/ubuntu18/2.x/updates/2.7.3.0/ambari.list
* apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B9733A7A07513CAD
* apt-get update
* apt-get install ambari-server
* ambari-server setup
* ambari-server setup –j /usr/java/default

# hadoop filesystem 설치
https://tlstjscjswo.tistory.com/entry/VM-Ubuntu-Hbase-%EC%84%A4%EC%B9%98

https://superkong1.tistory.com/41


# ubuntu 환경에서 hbase설치
1. 자바설치
* https://blog.naver.com/eon7500/221884844345
* $sudo apt-get update
* $java -version
* $ sudo nano /etc/environment 
* JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64" 
* $sudo nano /etc/environment 
* $ source /etc/environment
* $ echo $JAVA_HOME
* https://docs.cloudera.com/HDPDocuments/Ambari-2.7.3.0/bk_ambari-installation/content/install-ambari-server-ubuntu18.html

2. hbase설치
* https://tlstjscjswo.tistory.com/entry/VM-Ubuntu-Hbase-%EC%84%A4%EC%B9%98
* wget http://archive.apache.org/dist/hbase/1.2.3/hbase-1.2.3-bin.tar.g
* vi /etc/bash.bashrc 홈디렉토리
* /dev/app/hbase-1.2.3/conf/hbase-env.sh 주석막기
* /dev/app/hbase-1.2.3/conf/hbase-site.xml
<configuration>
        <property>
                <name>hbase.rootdir</name>
                <value>$HBASE_HOME/bin/hbase</value>
        </property>
</configuration>
*확인 http://localhost:16010/master-status

# Apache Spark=====
* pyspark설치
*  java_home classpath설치
*  conda install pyspark 
*  pyspark 

* 정규식 
* REGEXP_EXTRACT(value, regexp[, position[, occurrence]]) value에서 정규 표현식 regexp와 일치하는 첫 번째 하위 문자열을 반환합니다. 일치하는 항목이 없으면 NULL을 반환합니다.
* \d	숫자 0 ~ 9
* \w	문자를 의미
* \s	화이트 스페이스를 의미하는데, [\t\n\r\f] 와 동일

*  from pyspark.sql.types import *
*  spark.sql 정형데이터, StructType()으로 스키마 지정으로 속도향상, 
*  spark.read.csv('xxx.csv', header=True, schema=스키마StructType(), nullValue='NA')
*  Spark 데이터 추출 및 전처리, 출처 - https://wikidocs.net/16565

*  pyspark함수정리 :  출처 - https://jaeyung1001.tistory.com/59?category=767662
* from pyspark.sql import function as F
* 1) spark.read.csv   df.printSchema()    df.show(), df.filter(컬럼 조건).show(), df.groupBy(컬럼).count().show()
* 2) agg(*exprs)      df.agg(표현식 -> dataframe
* 3) alias(alias명)   df.alias(
* 4) cache()          df.cache() 메모리에 남겨두고 반복 조회 속도 향상
* 5) collect()        dataframe 모든 row반환
* 6) corr(col1, col2, method) correlation 상관관계, 상관계수
* 7) describe()       df.describe(NA/컬럼).show()
* 8) drop()           df.drop(테이블/컬럼).collect()
* 9) dropDuplicates   중복row 제거
* 10) dropna          null값이 포함된 row를 뺀 새로운 dataframe을 반환
* 11) dtypes          col별 데이터 타입 반환
* 12) printSchema()   dtypes과 유사하고 트리형태로 타입반환
* 13) orderBy, sort()
* 14) replace
* 15) select(* / 컬럼), selectExpr(표현식(컬럼),)
* 16) summary(row명 항목들 지정)
* 17) withColumn(컬럼명, 컬럼) , withColumn(컬럼명, lit(값지정))
* 18) between(범위1, 범위2) 범위1과 2사이에 존재하는지 true/false
* 19) contains(문자) 여부
* 20) F.when(조건, 실행)
* 21) where (col(컬럼명).isin(리스트)), where (col(컬럼명).isin(리스트)==False)
* 22) udf함수 function.udf(lambda z: 정렬기준, 리턴값의 데이터 형식 ArrayType(StringType())
* 23) join            table.alias(별칭1), table.alias(별칭2)   별칭1.join(별칭2, 별칭1.컬럼==별칭2.컬럼)
* from pyspark.sql import SQLContext
* dataframe_v = sqlContext.createDataFrame(pd.read_cdv("경로"))
* from pyspark.sql.types import *  sqlContext.createDataFrame(list, 타입).show() list자료형을 df자료형으로 넣을때

* Working with databases 어렵게 할필요없음
* import jpype   import jaydebeapi as jp    
* jpype.startJVM(jpype.getDefaultJVMPath(), '-Djava.class.path=C:\python-dev/ojdbc6.jar')
* conn = jp.connect('oracle.jdbc.OracleDriver','jdbc:oracle:thin:ID/pW@IP/SID') 
* cur = conn.cursor()      cur.execute("select * from    
* acc = cur.fetchall()   cur.close()   conn.close()  jpype.shutdownJVM()   print(acc)
* 출처, https://bongury.tistory.com/89
* 아래 한줄로 jdbc접속 가능 단 ojdbc6.jar는 spark모듈내 jar추가 필요
* spark.read.format("jdbc").options(url="jdbc:oracle:thin:ID/PW@호스트:1521/SID",dbtable="(조회문)",user="ID",password="PW",driver="oracle.jdbc.OracleDriver").load() 

* 실습문장
* ======SQLContext, pandas이용=============
* from pyspark.sql import SQLContext
* import pandas as pd 
* sqlContext=SQLContext(sc) 
* df=pd.read_csv(r'C:\Users\doc_use_log.csv')
* sdf=sqlContext.createDataFrame(df)
* 출처, 관련예제 - https://spark.apache.org/docs/latest/api/python/pyspark.sql.html#pyspark.sql.SparkSession

* ====SparkSession,SparkContext이용==========
* from pyspark.sql.session import SparkSession
* from pyspark import SparkContext
* sc = SparkContext()
* spark = SparkSession(sc)
* df = spark.read.option("header","true").csv(r'C:\Users\youngjin7.kim\doc_use_log.csv')

* ==== hdfs 에서 pyspark으로 파일 읽기 =========
* csvfile = spark.read.csv('hdfs://localhost:9000/test6/fct_data.csv')
* textfile = spark.read.csv('hdfs://localhost:9000/test6/out.txt')
* textfile = sc.textFile('hdfs://localhost:9000/test6/out.txt')
* rs_text = textfile.map(lambda x: (x, )).toDF()
* ==== hdfs 에서 text파일 pyspark으로 파일 읽기 =========
* textfile = sc.textFile('hdfs://localhost:9000/test6/out.txt')
* textfile_split = textfile.map(lambda x:x.split(";"))
* textfile_filted = textfile_split.filter(lambda x:"incheon" in x)
* textfile_filted.toDF().show()
* =======데이터프레임을 테이블 쿼리로 조회하기
* df2.registerTempTable("df_tmp2")
* df2 = spark.sql("select * from df_tmp2 where location = 'seoul'")

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

* S3로부터 csv 파일 읽기
* import boto3
* import pandas as pd
* aws_key= ""
* aws_secret = ""
* s3 = boto3.client('s3', 'ap-northeast-2', aws_access_key_id = aws_key, aws_secret_access_key = aws_secret)
* bucket = 'youngjin-kim'
* df = s3.get_object(Bucket = bucket, Key = 'result/xxxx.csv')
* df = pd.read_csv(df2['Body'])

* S3로부터 parquet 파일 읽기1
* import pyarrow.parquet as pq
* import s3fs
* s3a = s3fs.S3FileSystem()
* pandas_dataframe = pq.ParquetDataset('s3://youngjin-kim/result/part-00000-b362685d-4ed7-4a7f-b9c7-04e1f74aea0e-c000.snappy.parquet', * filesystem=s3a).read_pandas().to_pandas()

* S3로부터 parquet 파일 읽기2
* import boto3
* import io
* import pandas as pd
* def pd_read_s3_parquet(key, bucket, s3_client=None, args):
*     if s3_client is None:
*         s3_client = boto3.client('s3')
*     obj = s3_client.get_object(Bucket=bucket, Key=key)
*     return pd.read_parquet(io.BytesIO(obj['Body'].read()), args)
* pd_read_s3_parquet('result/part-00000-b362685d-4ed7-4a7f-b9c7-04e1f74aea0e-c000.snappy.parquet', bucket, s3)


* 출처 블로그 
*  https://frhyme.github.io/python-lib/pyspark/ 설치 튜토리얼
*  https://wikidocs.net/16565           개념정리
*  https://jaeyung1001.tistory.com/59   함수정리

# matplotlib.pyplot
* import matplotlib.pyplot as plt     
* 선 - plt.plot([1,2],[1,5])   
* 점/원형 - plt.scatter([1,2,3],[10,20,30],c='red',alpha=0.2)     
* 막대바 - plt.bar([1,2,3], [1,5,8], width=0.7, color="blue")
* import matplotlib.font_manager as fm
* plt.xlabel('POS번호', fontproperties=fm.FontProperties(fname='C:\Windows\Fonts\GULIM.ttc', size=50))
* plt.grid(b=True,which='both',axis='both')     plt.xscale('log')   plt.legend(['Mouse', 'Cat'])
* plt.hist(life_exp1950, bins=15)   plt.xticks([1,2,3],['1k','2k','3k']) plt.xlabel('x축이름')  plt.title('제목') 

# pyspark.ml
* from pyspark.ml import Pipeline
* from pyspark.ml.classification import LogisticRegression
* from pyspark.ml.feature import HashingTF, Tokenizer
* 관련학습 출처 https://spark.apache.org/docs/latest/ml-pipeline.html 
* 출처- https://docs.microsoft.com/ko-kr/azure/hdinsight/spark/apache-spark-machine-learning-mllib-ipython#construct-the-input-dataframe
1) pipeline(Estimator)
2) Pipeline.fit()
3) pipelineModel(Transformer)
4) pipelineModel.transform()

# AI학습
* 머신러닝 - 라이브러리 사이킷런(Scikit-learn) 데이터정리, 모델학습(서포트벡터머신,나이브베이즈), 모델평가(교차검증,파이프라인), 
* 출처 -  https://blog.naver.com/sundooedu/221275605087
* 딥러닝 - 텐서플로

# Scikit-learn
* 설치 pip install sckit-learn



# flask 파이선웹어플리케이션
* Python으로으로 구동되는 웹서버/프레임워크, Django 와 같은 한종류, 설치 pip install flask
* 출처, 학습 영상 - https://www.youtube.com/watch?v=u2KnTZa1_WU
* https://velog.io/@decody/%ED%8C%8C%EC%9D%B4%EC%8D%AC-Flask%EB%A1%9C-%EA%B0%84%EB%8B%A8-%EC%9B%B9%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99%ED%95%98%EA%B8%B0
* 실행 flask run - 최초 context 지점 app.py 5000포트 러닝
* app = Flask(__name__) @app.route('/') def index(): return render_template('index.html')
* 파이선으로 간단히 서버 구동시 python -m http.server 8080


# KONLPY 코엔엘파이
https://konlpy-ko.readthedocs.io/ko/v0.4.3/

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

# Vue.js
* 설치 npm i @vue/cli -g    npm i @vue/cli-service-global -g      vue --version       
* 프로젝생성 - vue create 프로젝트명 자동생성 후 npm run serve 실행
* 관련 학습 영상 https://www.youtube.com/watch?v=PxFPAlHPdSM
* 학습 블로그 https://cli.vuejs.org/guide/installation.html   
* https://kr.vuejs.org/v2/guide/index.html   
* 출처 https://codelabs-vue.web.app/

# Axios 
* HTTP통신을 위한 javascript라이브러리, 브라우저와 Node.js 사용, get,매개변수/post/Patch/delete Rest API
* HTTP 클라이언트 라이브러리로써, 비동기 방식으로 HTTP 데이터 요청을 실행
* 출처 - https://tuhbm.github.io/2019/03/21/axios/
* https://velog.io/@rohkorea86/%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B9%84%EB%8F%99%EA%B8%B0%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%B0%A8%EA%B7%BC%EC%B0%A8%EA%B7%BC-%EB%8B%A4%EB%A3%A8%EB%A0%A4%EA%B3%A0-%ED%95%A9%EB%8B%88%EB%8B%A4.

# React
* npm install -g create-react-app 설치 create-react-app hello-world
* 출처 - https://beomy.tistory.com/24#createReactApp

# socket.io
* 설치 npm install socket.io --save
* socket.on('connetion', function(~~ 소켓연결 
* socket.on('reply'/'event'/'disconnect' ~~~ ));
* socket.emit('broadccast' 전체/긴급공지~~
* socket.emit('message', {room: joinedroom, msg:msg, function~~~ 메세지전송
* socket.emit('join', roomid, ()=> ~~~ 방에조인
* socket.emit('rooms', function(rooms)~~~ 룸정보
* socket.emit("message-for-one", socketid, ~~ 귓속말
* socket.emit('leave', joinedRoom 조인된방에서 나가기
* 출처 - https://www.npmjs.com/package/socket.io

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
*  1) 스파크 RDD(Resilient Distributed Datase), 코어, SQL, Mlib, GraphX

*  cdn(contents Delivery Network) 
*  출처 - https://goddaehee.tistory.com/173
*  캐싱서버를 두고 리소스 로딩속도, 서버부하 감소 등 

*  프록시 서버
*  출처 - https://goddaehee.tistory.com/171?category=281064
*  다른 서버나 호스트 리소스 요청에 대한 중개 역할, 중개 혹은 네트워크 라우터, 프록시 서버는 캐싱가능
*  방화벽 네트워크상 에서 트래픽, 접근 우회 등 수행

*  Hive와 Spark 비교 
*  1) HiveQL로 분석, 데이터 작업은 용이하나, Mapreduce 변환되어 빠른 처리는 불가능 
*  2) Apache Spark 메모리 기반을 통해 성능, 속도향상
*  출처 - http://hochul.net/blog/about-hive-pig-spark_data/

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


# Python ==========
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

* import re 함수 compile 문
* 출처 - https://greeksharifa.github.io/%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D(re)/2018/07/20/regex-usage-01-basic/#match-object%EC%9D%98-%EB%A9%94%EC%84%9C%EB%93%9C%EB%93%A4
* p = re.compile("정규식 표현") 패턴 객체(p)를 만들고 나서 여러번 재사용이 가능하다. 반복적인 매칭 작업이 필요할 경우에는 패턴을 미리 컴파일
* re.match(pattern, string, flags) 문자열의 처음부터 시작하여 패턴이 일치되는 것이 있는지를 확인한다
* re.search(pattern, string, flags)  re.match와 비슷하지만, 반드시 문자열의 처음부터 일치해야 하는 것은 아니다.
* re.findall(pattern, string, flags) 정규식과 매치되는 모든 문자열을 리스트형식으로 리턴한다.
* re.finditer(pattern, string, flags) 정규식과 매치되는 모든 문자열을 iterator 객체로 리턴한다. 객체의 값을 불러오려면 for문을 이용
* re.fullmatch(pattern, string, flags) 는 패턴과 문자열이 남는 부분 없이 완벽하게 일치하는지를 검사한다

* matchObj = re.search('match', "'matchObj'~~~~
* matchObj.group()	일치된 문자열을 반환한다.
* matchObj.start()	일치된 문자열의 시작 위치를 반환한다.
* matchObj.end()	일치된 문자열의 끝 위치를 반환한다.
* matchObj.span()	일치된 문자열의 (시작 위치, 끝 위치) 튜플을 반환한다.

* \d	숫자 0 ~ 9
* \w	문자를 의미
* \s	화이트 스페이스를 의미하는데, [\t\n\r\f] 와 동일

* import numpy as np 집합함수 setfuction
* (1) np.unique(x) : 배열 내 중복된 원소 제거 후 유일한 원소를 정렬하여 반환
* (2) np.intersect1d(x, y) : 두 개의 배열 x, y 의 교집합을 정렬하여 반환
* (3) np.union1d(x, y) : 두 개의 배열 x, y의 합집합을 정렬하여 반환
* (4) np.in1d(x, y) : 첫번째 배열 x가 두번째 배열 y의 원소를 포함하고 있는지 여부의 불리언 배열을 반환
* (5) np.setdiff1d(x, y) : 첫번째 배열 x로 부터 두번째 배열 y를 뺀 차집합을 반환
* (6) np.setxor1d(x, y) : 두 배열 x, y의 합집합에서 교집합을 뺀 대칭차집합을 반환 
* 출처: https://rfriend.tistory.com/355 
* array 범위인덱스 arr[5:8] -> 인덱스가 5인것 부터 8전까지 즉 5,6,7 을 의미

# Pandas=========

*  import pandas as pd
  
*  csv_data = pd.read_csv('c:/dataset_file.csv',delimiter='\t')
*  csv_data

# numpy=================
* import numpy as np
* 행렬로 표현 np.arange(16) => 0,1,2,,15    .reshape(2,4) 2행4열   print(배열)

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
* 학습영상 https://www.youtube.com/watch?v=pc1jgmuS02M


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

* 로그수준 비정형 데이터를 가공하여 분석/모델링까지 도출할 수 있는 전체 분석 프로세스 전문가

* 관련 참고 영상 -https://www.youtube.com/watch?v=Buc_EgZO1ho
