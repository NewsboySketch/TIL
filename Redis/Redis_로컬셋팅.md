
# 버전
- EOL 일정 : https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/red-ug/deprecated-engine-versions.html
- 지원 버전 : https://docs.aws.amazon.com/ko_kr/AmazonElastiCache/latest/red-ug/supported-engine-versions.html
- 7.0 을 사용해보자. 얼리 어답터니까

# 도커로 이미지 다운
- https://hub.docker.com/_/redis

```shell
# 1. redis 이미지 다운로드
docker pull redis:7.0

# 2. 설치된 이미지 확인
docker images
```
```shell
REPOSITORY        TAG         IMAGE ID          CREATED           SIZE
redis             7.0         d9c89935bd08      3 weeks ago       130MB
```
```shell
# 사용할 포트가 사용중인지 확인
lsof -i:6379
```

**`docker run` 실행 옵션들**
- `-d` : 어떤 이미지 사용할건지
- `--name` : 컨테이너 이름 지정
- `-p` : 호스트 포트:컨테이너 포트
- `-i` : standard input 활성화. 접속해서 명령어 i/o 가능해짐
- `-t` : 터미널을 사용하도록 설정
- 추후에 볼륨설정, timezone, config 추가로 알아봐야함

redis 올리자마자 해킹 당할 수 있기 때문에 환경변수로 비밀번호를 같이 줬다.
일단 레디스 프로세스 테스트용이기때문에 터미널이랑 i/o는 없어도 될 것 같음
```shell
docker run -p 6379:6379 --name redis -d redis:7.0 --requirepass {password}
```

### DB 툴 통해 로그인
6379 포트로 접속하면 redis 실행된 것 확인 가능하다.   
모니터링 방법으로 redisinsight 라는것도 있다고 함. 추후에 사용 예정    
원래 사용중이던 툴(TablePlus)로 접근해봤음     

<img src="https://github.com/NewsboySketch/TIL/assets/84266499/b071d6ef-7a5b-47f2-af78-52725b4ad9f1" width="460"/>    

아직 아무 item도 없다.   
<img src="https://github.com/NewsboySketch/TIL/assets/84266499/ee9d1a71-ab52-4155-b132-cf55a4a718fc" width="460"/>    

### CLI로 로그인
```shell
# redis-cli 로그인
redis-cli -h localhost -p 6379 -a {password}
```
요런 워닝 메시지가 뜨는데, `Warning: Using a password with '-a' or '-u' option on the command line interface may not be safe.`
패스워드를 명령줄 라인에 바로 입력하는 것은 위험하다는 뜻. username이 있는 명령어의 경우 

# Redis의 Data Types
이제부터 여기 있는 data types 모두 사용해볼 예정    
https://redis.io/docs/data-types/       
https://redis.io/docs/get-started/

## 1. String
byte sequence를 저장하는 Redis의 가장 기본적인 데이터 타입이다.(text, serialized objects, binary array 등 ...)     
캐싱이나 비트 연산에 주로 사용됨
### 1.1. get, set
```shell
# set 키워드로 저장하고
localhost:6379> set key1 value1
OK

# get 키워드로 읽을 수 있다.
localhost:6379> get key1
"value1"

# 존재하지 않는 키워드를 읽는 경우 nil
localhost:6379> get key2
(nil)
```
이미 존재하는 key로 set하는 경우, 기존의 value는 replace됨     
value는 jpeg같은것도 가능하며, 512M까지 저장할 수 있다.

### 1.2. nx
nx 옵션을 통해 덮어쓰기를 막을 수 있다.
```shell
localhost:6379> set key1 value0 nx
(nil)
localhost:6379> get key1
"value1"
localhost:6379> set key1 value0 xx
OK
localhost:6379> get key1
"value0"
```

### 1.3. getset
이전의 값을 반환하고 새로운 값을 삽입한다.   
조회 시 1씩 증가, 이런 로직 짤 때 사용할 수 있을것임
```shell
localhost:6379> getset key1 value2
"value1"
localhost:6379> get key1
"value2"
```

### 1.4. mset, mget
다수의 객체들을 한꺼번에 set, get하는 명령어. latencty가 중요한 상황에서 쓸 수 있을 것    
mget으로 객체 조회 시 array 타입으로 반환된다. 
```shell
localhost:6379> mset key1 value1 key2 value2 key3 value3
OK
localhost:6379> mget key1 key2 key3
1) "value1"
2) "value2"
3) "value3"
```