---
layout: post
title: "Migration Workshop"
toc: true
categories: "Migration"
---

## Migration
---
- Server Migration
- Database Migration
- NAS Migration
- Hybrid Cloud Storage

## 마이그레이션 단계
1. 평가단계
2. 준비 및 계획 단계
3. 마이그레이션 단계
- CloudEndure
- DMS
- Datasync
- Storage Gateway

## CloudEndure
---
### 작동방식
- CloudEndure Agent 설치
- OS에 mapping되어 있는 Block Device 정보만 복제됨.

### 네트워크 구성
- 프로젝트 : DR or Migration


## Database Migration Service
---
### Challenge
- 높은비용
- 복잡한 설정
- Downtime
- DB별 application 코드 수정

### 특징
- Onpremise와 AWS 간 마이그레이션
- 동종/이기종 마이그레이션
- 자동 Schema 변환
- Downtime 최소화
- 다양한 소스, 타겟 지원

### 구성
1. 복제 인스턴스(EC2) 구성
2. 원본/대상 DB 접속 구성
3. 복제 Task 생성
4. 복제 모니터링

### 복제 작업
- Migration Type : Full load, CDC, Full load and CDC

### 기능
- Pararell
- 데이터 통합
- 데이터 분리
- 데이터 필터링 : 원하는 Table만 선별

### 순서
1. 복제 인스턴스 구동
2. 소스와 목적지 연결
3. DB, 스키마, Table 선택
4. DMS가 타겟 오브젝트 생성
5. DMS가 데이터 이동 및 동기화
6. 애플리케이션을 신규 DB로 변경

### 변경 데이터 캡처(CDC, Change Data Capture)

### DMS 비용
- 복제 인스턴스 비용
- 데이터 비용
    - DMS로 전송되는 비용 무료
    - 동일 AZ내 무료

### AWS Schema Conversion Tool (SCT)
이기종 DB간 마이그레이션에서 DB 스키마 및 코드 변환 작업을 자동화


## AWS Datasync
---
### 단계

1. 에이전트 배포, 에이전트와 AWS 연결
- VMware ESXi OVA 제공
- AWS Snowcone으로 전송 가능

2. 작업 생성
- 소스, 타겟 스토리지 연결
- On-premise NFS 파일서버 => Amazon S3 or Amazon EFS

3. 작업 실행

### 작동방식
1. 에이전트 배포
2. 데이터 전송
3. 타겟 스토리지에 데이터 읽거나 씀

### NFS 서버 이전
<img src="/assets/images/2020-11-11.png" alt="StorageMigration">

1. DataSync는 S3로 마이그레이션한다. 증분 복사본이 S3를 최신 상태로 유지.

2. 지연 시간에 민감한 애플리케이션이 Storage Gateway를 통해 S3에 액세스

3. On-Premise의 NFS 스토리지를 줄임

### Amazon EFS
- AWS 공식 문서 확인


## AWS Storage Gateway
---
### On-premise Storage Challenges
- 백업 인프라 운영 비용 증가
- 스토리지의 용량 wpdir
- 클라우드 데이터에 대한 접근이 느리고 제약됨

### Storage Gateway - 사용 사례 3
- 온프레미스에서 무한의 클라우드 스토리지에 연결하는 통로
1. 백업 인프라 운영 비용 증가
- 백업을 클라우드로 이관
2. 스토리지의 용량 제약
- 클라우드 기반 파일 공유로 전환
3. 클라우드 데이터에 대한 접근이 느리고 제약됨
- 클라우드 데이터를 애플리케이션 수정없이 접근 가능

### 패밀리
1. 파일 게이트웨이 (NFS, SMB)
- 로컬 Cache 기능이 있는 파일 게이트웨이에서 Amazon S3에 파일을 읽기 및 저장

2. 볼륨 게이트웨이 (iSCSI)
- Amazon EBS를 통해

3. 테이프 게이트웨이 (iSCSI VTL)

<img src="/assets/images/2020-11-11_1.png" alt="StorageGateway">
- Storage Gateway는 VM형태로 설치됨.
- 호스트 플랫폼: VMware ESXi, Hyper-V, Linux KVM, EC2, 하드웨어 어플라이언스
- AWS 서비스와 통합: IAM, KMS, CloudTrail, CloudWatch

### File gateway
- S3를 로컬에 있는 것처럼 사용 가능하게 함

#### 기능
- 데이터 및 메타데이터를 캐시하여 Low Latency로 S3 데이터 접근
- Write시 캐시에 먼저 쓰고, 변경된 데이터만 s3에 병렬 multi-part PUT

### Volume gateway
- S3와 EBS Snapshot으로 백업되는 On-Premises 블록 스토리지

#### 기능
- 사내 볼륨의 EBS 스냅샷을 작성하여 클라우드에 저장
- Cached mode와 Stored mode 지원
- DR, Data migration

### Tape gateway
- 문서 참고

## File Gateway
--
### 배포 옵션
- Virtual machines
- Hardware appliance

### On-premise 백업

### 비용
- 스토리지
- 요청 당

## Migration 실습 안내
---
https://bit.ly/3mgDmSD
http://awsmigration-workshop.s3-website.ap-northeast-2.amazonaws.com/ko/lab4/