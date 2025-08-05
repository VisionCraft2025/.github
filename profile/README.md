# VisionCraft 2025 - 스마트 팩토리 통합 시스템

> **패트병 카메라 기반 분류 스마트 팩토리 시스템**  
> AI 기반 품질 관리와 실시간 모니터링을 통한 차세대 제조업 솔루션

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Qt](https://img.shields.io/badge/Qt-6.0+-green.svg)](https://www.qt.io/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-blue.svg)](https://opencv.org/)
[![C++](https://img.shields.io/badge/C++-17-red.svg)](https://isocpp.org/)


---

## 시스템 소개 영상

<div align="center">
  <video width="800" autoplay muted loop>
    <source src="https://private-user-images.githubusercontent.com/94597315/473916230-1ddf128f-e7c4-48ad-8385-efd2fcbd4e31.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTQyOTI5NTMsIm5iZiI6MTc1NDI5MjY1MywicGF0aCI6Ii85NDU5NzMxNS80NzM5MTYyMzAtMWRkZjEyOGYtZTdjNC00OGFkLTgzODUtZWZkMmZjYmQ0ZTMxLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODA0VDA3MzA1M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTgxYjNjZGIzMTQ1MjU2OWFlM2M2OGIxOTcwMzE3OTBmODA5NmM0MDA5NDUyZGRiNjUwZDNkMTEwZjEzZTM5Y2QmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.VEew_jQkgBxkeMlPP9BWHcfTxsrP94zFJAe-ZDzMlRU" type="video/mp4">
  </video>
  <p><em>VisionCraft 2025 - 카메라 기반 스마트 팩토리 통합 시스템</em></p>
</div>

---

## 프로젝트 개요

**VisionCraft 2025**는 컴퓨터 비전과 AI 기술을 활용하여 패트병을 자동으로 분류하고 품질을 관리하는 통합 스마트 팩토리 시스템입니다. 실시간 영상 처리, MQTT 기반 IoT 통신, AI 챗봇을 통한 자연어 제어 등 최신 기술을 융합한 차세대 제조업 솔루션을 제공합니다.

### 핵심 목표
- **자동화된 품질 관리**: 카메라 기반 패트병 분류 및 불량품 감지
- **실시간 모니터링**: 공장 전체 장비 상태 통합 관리
- **AI 기반 제어**: 자연어 명령을 통한 직관적인 장비 제어
- **데이터 기반 의사결정**: 실시간 통계 분석 및 성능 최적화

---

## 시스템 아키텍처

```
┌─────────────────────────────────────────────────────────────────┐
│                    통합 서버 (*.kwon.pics)                      │
├─────────────────┬─────────────────┬─────────────────┬───────────┤
│   MQTT Broker   │   MCP Server    │   Video Server  │ Auth/TOTP │
│   (IoT 통신)     │   (AI Backend)  │   (RTSP/HTTP)   │ (보안)     │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│     MongoDB     │  Gemini API     │  영상 저장소     │  사용자DB  │
│   (데이터베이스)  │  (AI 처리)       │  (녹화 파일)     │  (인증)    │
└─────────────────┴─────────────────┴─────────────────┴───────────┘
                                    ▲
                                    │ MQTT/HTTP/RTSP
                                    ▼
┌─────────────────────────────────────────────────────────────────┐
│                      Qt Client (GUI App)                       │
├─────────────────┬─────────────────┬─────────────────┬───────────┤
│   메인 대시보드   │   피더 제어      │   컨베이어 제어   │  AI 챗봇   │
│   (Home)        │  (MainWindow)   │  (Conveyor)     │  (MCP)    │
└─────────────────┴─────────────────┴─────────────────┴───────────┘
                                    ▲
                                    │ 제어 명령
                                    ▼
┌─────────────────────────────────────────────────────────────────┐
│                      공장 IoT 장비                              │
├─────────────────┬─────────────────┬─────────────────┬───────────┤
│     피더 1,2     │   컨베이어 1,2,3  │    로봇팔       │  카메라    │
│   (Feeder)      │   (Conveyor)    │  (Robot Arm)    │ (CCTV)    │
└─────────────────┴─────────────────┴─────────────────┴───────────┘
```

---

## 주요 기능

### 1. 실시간 영상 처리 시스템
- **패트병 감지**: SAD(Sum of Absolute Differences) 알고리즘 기반 고속 객체 감지
- **품질 분석**: 머신러닝 기반 투명/유색 패트병 분류
- **RTSP 스트리밍**: 실시간 영상 전송 및 원격 모니터링
- **ROI 설정**: 관심 영역 지정을 통한 정밀 감지

### 2. 스마트 팩토리 제어
- **피더 시스템**: 정/역방향 회전, 속도 제어, RPM 모니터링
- **컨베이어 시스템**: 다중 컨베이어 제어, 자동 순환, 서보 연동
- **로봇팔 제어**: 4축 서보 모터 기반 정밀 제어
- **통합 제어**: 전체 공장 라인 동기화 및 자동화

### 3. AI 챗봇 시스템
- **자연어 처리**: Google Gemini 2.5 Flash 모델 활용
- **스마트 제어**: "피더1 켜줘", "컨베이어 상태 확인해줘" 등 직관적 명령
- **실시간 데이터 조회**: "오늘 에러 통계 보여줘", "불량률 분석해줘"
- **MCP 통합**: Model Context Protocol 기반 도구 연동

### 4. 데이터 분석 및 시각화
- **실시간 차트**: Qt Charts 기반 동적 성능 그래프
- **품질 통계**: 불량률, 양품률 분석 및 트렌드 추적
- **성능 모니터링**: 장비별 속도, 처리량, 가동률 추적
- **예측 분석**: 과거 데이터 기반 성능 예측

### 5. 보안 및 인증
- **TOTP 2FA 인증**: Google Authenticator 연동 6자리 OTP 코드 기반 다단계 인증
- **모바일 연동**: 스마트폰 앱을 통한 실시간 보안 코드 생성
- **TLS 암호화**: MQTT 통신 및 데이터 전송 보안
- **권한 관리**: 역할 기반 장비별 접근 권한 제어
- **감사 로그**: 모든 제어 명령 및 접근 기록

---

## 기술 스택

### Frontend & UI
- **Qt 6**: 크로스플랫폼 GUI 프레임워크
- **C++17**: 고성능 시스템 프로그래밍
- **OpenCV 4.x**: 컴퓨터 비전 및 영상 처리
- **Qt Charts**: 실시간 데이터 시각화

### Backend & Communication
- **MQTT**: IoT 장비 간 실시간 통신
- **HTTP REST API**: MCP 서버 통신
- **RTSP**: 영상 스트리밍 프로토콜
- **WebSocket**: 실시간 데이터 스트리밍

### AI & Data Processing
- **Google Gemini API**: 자연어 처리 및 AI 추론
- **MongoDB**: NoSQL 데이터베이스
- **MCP (Model Context Protocol)**: AI 도구 통합 프로토콜
- **TensorFlow/OpenCV ML**: 품질 분석 모델

### Hardware & Embedded
- **Raspberry Pi 4**: 엣지 컴퓨팅 플랫폼
- **libcamera**: 카메라 인터페이스
- **GPIO 제어**: 서보모터, 스테퍼모터 제어
- **GStreamer**: 멀티미디어 파이프라인

---

## 프로젝트 구조

```
VisionCraft-2025/
├── client_qt/              # Qt 기반 통합 클라이언트
│   ├── ui/                    # 사용자 인터페이스
│   ├── mcp/                   # AI 챗봇 시스템
│   ├── video/                 # 영상 처리 모듈
│   ├── charts/                # 데이터 시각화
│   └── widgets/               # 커스텀 UI 컴포넌트
├── factory/                # 공장 장비 제어 시스템
│   ├── conveyor01_nonstop_ver3/  # 컨베이어 제어
│   ├── feeder_mqtt/           # 피더 제어
│   ├── robot_arm_mqtt/        # 로봇팔 제어
│   └── conveyor02_tls_mqtt/   # 보조 컨베이어
├── Image-Processing/       # 영상 처리 시스템
│   ├── conveyor_rtsp_tls/     # 컨베이어 카메라
│   └── feeder_rtsp_tls_ver2/  # 피더 카메라
├── bottle_pusher/          # 패트병 감지 시스템
├── DBMS_with_MQTT/        # 데이터베이스 연동
├── MFA_server/             # 다단계 인증 서버
├── QT_video_viewer/        # 영상 뷰어 클라이언트
├── server_rpi/             # 라즈베리파이 서버
└── factory_monitor/        # 공장 모니터링 도구
```

---

## 시스템 데모

### 통합 대시보드
<div align="center">
  <video width="800" autoplay muted loop>
    <source src="https://private-user-images.githubusercontent.com/94597315/473920182-2aaa46a5-373c-43df-bfe3-ab83b221973f.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTQyOTI5NTMsIm5iZiI6MTc1NDI5MjY1MywicGF0aCI6Ii85NDU5NzMxNS80NzM5MjAxODItMmFhYTQ2YTUtMzczYy00M2RmLWJmZTMtYWI4M2IyMjE5NzNmLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODA0VDA3MzA1M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPThjMGU1MjRiMzgwODhlMTllZGQ2MDA3ZTY2OTg1NTEyMjdkNGQxYjYxOWI5MGZkNjdjYzA5MWVmMmQyOWJmMjcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.pLMg3kN6ChoxA1baPzOVHG4oh0Eef2AvJS6SQJDArMA" type="video/mp4">
  </video>
  <p><em>Qt 기반 통합 모니터링 대시보드 - 3채널 카메라 동시 모니터링</em></p>
</div>

### 실시간 패트병 감지 시연
<div align="center">
  <video width="800" autoplay muted loop>
    <source src="https://private-user-images.githubusercontent.com/94597315/473921393-41d30105-c2d2-4065-a19f-3be9ecf568c5.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTQyOTMxMDgsIm5iZiI6MTc1NDI5MjgwOCwicGF0aCI6Ii85NDU5NzMxNS80NzM5MjEzOTMtNDFkMzAxMDUtYzJkMi00MDY1LWExOWYtM2JlOWVjZjU2OGM1Lm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODA0VDA3MzMyOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTJjZWRkZjk3NTAyMjgxMDk4NzQ2ZmE4MWFiZjFkNjI1MmFlYjk3NDkxZDc2ZTkzZTk5N2FiZTg5ZGM3MWE4ZjgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.djWgFcfBg3eQK44AiMuO5OYK-q6dr19GH1RzQwZR5Xs" type="video/mp4">
  </video>
  <p><em>실시간 카메라를 통한 패트병 자동 감지 및 분류 과정</em></p>
</div>

### TOTP 기반 보안 로그인
<div align="center">
  <video width="600" autoplay muted loop>
    <source src="https://private-user-images.githubusercontent.com/94597315/473916229-7da337ba-5e13-4479-a7ac-9cc15653d78b.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTQyOTI5NTMsIm5iZiI6MTc1NDI5MjY1MywicGF0aCI6Ii85NDU5NzMxNS80NzM5MTYyMjktN2RhMzM3YmEtNWUxMy00NDc5LWE3YWMtOWNjMTU2NTNkNzhiLm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA4MDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwODA0VDA3MzA1M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTViMGMxNTBiMTE1ZjMzOWYxMjkwNGY2YjE5MGQ3NmY2OTEzN2FkYTA5Mjg3ODVhN2VhZTRlNjMxM2EyYjQ1NWYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.NVjaa6NprHwjU-48l07JR6mm_jKx0r971Z8sw-VSwPY" type="video/mp4">
  </video>
  <p><em>Google Authenticator 연동 6자리 OTP 코드 기반 다단계 인증</em></p>
</div>

---

## 핵심 모듈 상세

### 1. 패트병 감지 시스템 (bottle_pusher)
```cpp
// 고속 SAD 알고리즘 기반 실시간 감지
double calculateFastSAD(const cv::Mat &current, const cv::Mat &previous, const cv::Mat &mask) {
    cv::Mat diff;
    cv::absdiff(current, previous, diff);
    cv::Mat maskedDiff;
    cv::bitwise_and(diff, mask, maskedDiff);
    return cv::sum(maskedDiff)[0];
}
```

**주요 특징:**
- 320x240 @ 30FPS 고속 처리
- ROI 기반 정밀 감지
- TCP/RTSP 원격 제어
- 서보모터 자동 제어

### 2. AI 챗봇 시스템 (MCP Agent)
```cpp
// Gemini API 통합 파이프라인
void MCPAgentClient::executeUnifiedPipeline(const QString& userQuery) {
    QString prompt = generateUnifiedPrompt(userQuery);
    setPipelineState(PipelineState::DISCOVERING_TOOL);
    sendGeminiRequest(prompt);
}
```

**지원 명령어:**
- "피더1 켜줘" → MQTT 제어
- "컨베이어 상태 확인해줘" → 상태 조회
- "오늘 에러 통계 보여줘" → 데이터 분석

### 3. 통합 클라이언트 (client_qt)
- **메인 대시보드**: 전체 시스템 모니터링
- **장비별 제어**: 피더, 컨베이어, 로봇팔 개별 제어
- **실시간 영상**: 3채널 동시 모니터링
- **데이터 시각화**: 성능 차트 및 통계 분석

---

## 성능 지표

### 영상 처리 성능
- **처리 속도**: 30 FPS @ 320x240
- **감지 정확도**: 95%+ (ROI 설정 시)
- **응답 시간**: < 100ms
- **RTSP 지연**: < 200ms

### 시스템 성능
- **MQTT 처리량**: 1000+ msg/sec
- **동시 연결**: 50+ 클라이언트
- **데이터 처리**: 10MB/min
- **가동률**: 99.5%+

---

## 설정 및 커스터마이징

### MQTT 토픽 구조
```
factory/
├── feeder_01/cmd          # 피더 제어 명령
├── feeder_01/status       # 피더 상태 응답
├── conveyor_03/cmd        # 컨베이어 제어
├── robot_arm_01/cmd       # 로봇팔 제어
└── hanwha/cctv/zoom       # 카메라 제어
```

### AI 챗봇 도구 목록
- `db_find`: MongoDB 로그 조회
- `device_control`: HTTP 기반 장비 제어
- `mqtt_device_control`: MQTT 실시간 제어
- `conveyor_failure_stats`: 불량률 통계
- `device_statistics`: 성능 통계

---

## 모니터링 및 분석

### 실시간 대시보드
- 장비별 상태 모니터링
- 성능 지표 실시간 추적
- 오류 로그 및 알림
- 품질 통계 시각화

### 데이터 분석
- 일/월별 생산량 분석
- 불량률 트렌드 분석
- 장비 성능 최적화
- 예측 유지보수

---

## 보안 기능

### 인증 및 권한
- **TOTP 2FA**: Google Authenticator 호환
- **TLS 암호화**: 모든 통신 암호화
- **역할 기반 접근**: 사용자별 권한 관리
- **감사 로그**: 모든 활동 기록

### 네트워크 보안
- **mTLS**: 상호 인증서 기반 통신
- **VPN 지원**: 원격 접속 보안
- **방화벽 연동**: 네트워크 레벨 보안

---

## 기여 가이드

### Git 커밋 컨벤션
```
Feat/#이슈번호: 새로운 기능 구현
Fix/#이슈번호: 버그 수정
Docs/#이슈번호: 문서 업데이트
Chore/#이슈번호: 코드 정리
```

### 개발 워크플로우
1. 이슈 생성 및 브랜치 생성
2. 기능 개발 및 테스트
3. Pull Request 생성
4. 코드 리뷰 및 머지

---