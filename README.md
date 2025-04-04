# smartalloc-infra

---

## 📦 포함된 서비스

### 🔹 Kafka + Zookeeper
- 이미지: `confluentinc/cp-kafka:7.5.0`, `cp-zookeeper:7.5.0`
- 포트: `9092`, `2181`

### 🔹 MySQL 8.0
- 포트: `3306`
- 기본 DB: `mvp`
- 계정: `devteam` / 비밀번호: `devteam`

---

## 🚀 설치 및 실행 방법

### 1. Docker & Docker Compose 설치 확인

```bash
docker --version
docker-compose --version
```


### 2. Kafka & Zookeeper 실행
```
docker-compose -f kafka-compose.yml up -d
```


### 3. MySQL 실행
```
docker-compose -f mysql-compose.yml up -d
```
- MySQL은 포트 3306에서 실행됩니다.
- 접속 정보:
  - host: localhost
  - user: devteam
  - password: devteam
  - database: mvp
 

### 4. 실행 확인
```
docker exec -it kafka kafka-topics --bootstrap-server localhost:9092 --list
docker exec -it mysql mysql -u devteam -pdevteam -Dmvp
```


### 5. 종료 및 정리
```
docker-compose -f kafka-compose.yml down
docker-compose -f mysql-compose.yml down

## 완전 삭제 (MySQL)
docker-compose -f mysql-compose.yml down -v
```
