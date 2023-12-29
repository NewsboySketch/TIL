
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

6379 포트로 접속하면 redis 실행된 것 확인 가능하다.   
모니터링 방법으로 redisinsight 라는것도 있다고 함. 추후에 사용 예정    
원래 사용중이던 툴(TablePlus)로 접근해봤음     

![image](https://github.com/NewsboySketch/TIL/assets/84266499/b071d6ef-7a5b-47f2-af78-52725b4ad9f1)      
아직 아무 item도 없다.   
![image](https://github.com/NewsboySketch/TIL/assets/84266499/ee9d1a71-ab52-4155-b132-cf55a4a718fc)


# Redis의 Data Types
이제부터 여기 있는 data types 모두 사용해볼 예정    
https://redis.io/docs/data-types/       
https://redis.io/docs/get-started/    


