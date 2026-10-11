[architecture.md](https://github.com/user-attachments/files/33305924/architecture.md)
# Lab Architecture

## 구성

```text
              corp.local
                  |
          +-------+-------+
          |               |
         DC1             DC2
 Windows Server 2025  Windows Server 2025
   Domain Controller   Additional DC
          |               |
          +-------+-------+
                  |
               CLIENT01
              Windows 11
             Domain Client
```

위 그림은 **논리적인 도메인 구성도**이며 물리적 네트워크 배치나 가상 스위치 구조를 나타내지 않습니다.

## 실습 역할

| 시스템 | 역할 및 수행 내용 |
| --- | --- |
| DC1 | `corp.local` 도메인의 첫 번째 도메인 컨트롤러 |
| DC2 | 동일 도메인에 추가한 도메인 컨트롤러; DC 간 복제 상태 점검 |
| CLIENT01 | `corp.local` 도메인 참여 및 정책 적용 실습에 사용한 Windows 11 클라이언트 |

## 디렉터리 및 정책

- OU, 사용자, 그룹 객체 생성
- GPO 생성 및 정책 적용 실습
- DC1과 DC2 사이의 복제 상태 확인

특정 사용자에게 어떤 접근 권한을 위임했는지 또는 개별 GPO가 어떤 최종 값을 적용했는지는 이 문서에서 검증 결과로 주장하지 않습니다.

## 실습 범위

단일 도메인, 두 대의 도메인 컨트롤러, 한 대의 클라이언트를 사용한 개인 실습입니다. 다중 Forest 아키텍처, 기업 규모의 장애 대응, 실제 운영 절차는 재현하지 않았습니다.
