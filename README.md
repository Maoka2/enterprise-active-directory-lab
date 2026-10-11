[README.md](https://github.com/user-attachments/files/33305968/README.md)
# Enterprise Active Directory Home Lab

Windows Server를 활용해 Active Directory의 도메인, 계정, 그룹 정책, 도메인 컨트롤러 복제를 학습한 **개인 가상 환경 구성 실습**입니다.

> 실제 기업 Active Directory 운영 경험이 아닌 개인 Home Lab 기록입니다.

## 구성 환경

| 시스템 | 운영체제 | 실습 역할 |
| --- | --- | --- |
| DC1 | Windows Server 2025 | 첫 번째 Domain Controller |
| DC2 | Windows Server 2025 | 추가 Domain Controller |
| CLIENT01 | Windows 11 | 도메인에 참여한 클라이언트 |
| Domain | `corp.local` | 실습용 도메인 |

자세한 구성은 [Architecture](docs/architecture.md)에 정리했습니다.

## 직접 실습한 내용

- AD DS 설치 및 `corp.local` 도메인 구성
- 추가 Domain Controller 구성과 복제 상태 확인
- Windows 11 클라이언트 도메인 참여
- OU, 사용자, 그룹 생성
- GPO 생성 및 정책 적용 실습
- `repadmin`을 이용한 복제 오류 확인과 재검증

## 장애 진단 및 검증

DC 간 복제 상태를 점검하는 과정에서 **8524 (DNS lookup failure)** 오류를 확인했습니다.

`repadmin /replsummary`, `repadmin /showrepl`로 복제 상태를 점검하고 DNS 관련 설정을 확인했습니다. 이후 복제를 재수행했을 때 `SyncAll terminated with no errors.` 메시지를 확인했으며, 다시 실행한 `repadmin /replsummary`에서 **복제 실패 건수 0**을 확인했습니다.

당시 DNS 오류의 정확한 근본 원인과 복제 재수행 명령의 옵션은 기록만으로 확정하지 않았습니다.

진단 과정과 확인 범위: [Troubleshooting](docs/troubleshooting.md)

## 배운 점과 한계

이번 실습을 통해 서비스 구성 완료와 실제 정상 동작 확인은 별개라는 점을 경험했습니다. 문제가 생겼을 때 오류 메시지와 진단 명령으로 상태를 확인하고, 조치 후 같은 기준으로 재검증하는 과정을 중점적으로 학습했습니다.

이 저장소는 **2대의 DC와 1대의 클라이언트로 구성한 개인 실습**을 다룹니다. 기업의 대규모 AD 환경이나 실제 보안사고 대응 경험을 의미하지 않습니다. AD CS, WSUS, MECM, Entra ID 하이브리드 동기화 등은 이 저장소에서 구축·검증한 성과로 기재하지 않았습니다.

## 문서

- [Architecture](docs/architecture.md)
- [Troubleshooting — DC 복제 오류](docs/troubleshooting.md)
