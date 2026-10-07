# 이호철 · ho72

**AI 모델을 서비스에 연결하고, 반복 작업을 줄이는 도구를 만듭니다.**

반려견 안구 이미지의 질환 분류·설명 모델을 학습하고, 분산 서버의 모니터링을 구성했습니다. 생활 속 필요에서 출발한 웹서비스도 직접 개발·운영하고 있습니다. 데이터와 모델뿐 아니라, 결과를 사용하는 화면과 서비스를 유지하는 과정까지 관심을 두고 있습니다.

## 대표 프로젝트

### [PET-I — 반려견 안구 질환 분류·설명 VLM](https://github.com/ho72/pet-i-vlm-diagnosis)

안구 사진의 질환 분류와 증상 설명, 검색 근거를 활용한 후속 질의응답을 연결한 **4인 졸업프로젝트**입니다.

- **담당:** 설명형 학습 데이터 생성·전체 전처리, VLM 학습·검증, YOLO 학습·패딩 크롭, 검색 컨텍스트 파이프라인 구현
- **결과:** 7개 분류·700장 평가에서 정확도 **0.7400**, Macro F1 **0.7404** · 건국대학교 **2025학년도 생성형 AI 활용 사례 공모전 우수상**
- **기술:** Python · PyTorch · Qwen3-VL-8B · LoRA/Unsloth · YOLOv8

[전체 소개·평가 결과](https://github.com/ho72/pet-i-vlm-diagnosis) · [설명형 데이터 생성 코드](https://github.com/ho72/pet-i-explanation-data)

### [TacticAI — AI 대전 플랫폼의 Kubernetes 모니터링](https://github.com/ho72/tacticai-monitoring)

게임 처리·AI 추론·API Gateway를 분리한 **4인 팀 프로젝트**에서 서비스와 Pod의 상태를 수집·시각화하는 모니터링을 담당했습니다.

- **담당:** Prometheus Operator 기반 메트릭 수집, Grafana 대시보드, Pod 확장 시 자동 수집 검증
- **검증:** Mock-up 환경에서 AI Server Pod를 **3개 → 5개**로 늘려, 설정 변경 없이 신규 Pod의 지표가 수집·표시되는 것을 확인
- **기술:** Kubernetes · Prometheus · Grafana · Docker

[본인 작업·검증 화면](https://github.com/ho72/tacticai-monitoring) · [팀 프로젝트 조직](https://github.com/KU-TacticAI)

### [회의록 생성기 — 음성 전사부터 검토·보관까지](https://github.com/ho72/meeting-notes-generator)

회의 음성을 로컬 Whisper로 전사하고, **사용자가 수정한 전사문**을 바탕으로 AI 회의록을 만드는 개인 웹 도구입니다.

- **구현:** 음성 업로드·진행 상태 표시, 전사·회의록 편집, 템플릿 기반 생성, 저장·Markdown 다운로드, 이전 작업 재조회
- **설계:** 편집 내용 반영, 작업 대기열·처리 제한, 생성 실패 처리, 회귀 테스트와 GitHub Actions
- **기술:** Python · FastAPI · faster-whisper · Gemini API · JavaScript

## 개인 웹서비스 개발·운영

생활 속 필요를 해결하기 위해 서비스를 기획하고, AI 코딩 도구를 활용해 구현·개선하고 있습니다. **공통 인증 서버**에 사진·파일 공유, 스마트홈 관리, AI 개발 워크스페이스를 연결하고, 각 서비스의 데이터는 별도로 관리합니다.

| 서비스 | 구현한 기능 | 공개 코드 |
| --- | --- | --- |
| 사진·파일 공유 | 앨범 권한, 사진·영상 처리, 파일 공유 | [home-media-sharing](https://github.com/ho72/home-media-sharing) |
| 스마트홈 통합 관리 | 기기 제어, 자동화, 알림 | [smart-home-manager](https://github.com/ho72/smart-home-manager) |
| AI 개발 워크스페이스 | 브라우저에서 코딩 에이전트와 작업, 대화·첨부파일 보관, Git 변경 확인 | [ai-coding-workspace](https://github.com/ho72/ai-coding-workspace) |
| 공통 인증 | 소셜 로그인, JWT·Refresh Token, 사용자 프로필, 서비스 연동 | [unified-auth-server](https://github.com/ho72/unified-auth-server) |

## 경험과 학습

- **건국대학교 컴퓨터공학부 졸업** — VLM 졸업프로젝트와 분산 시스템 팀 프로젝트 수행
- **소프트웨어 개발 실무** — AI 문서 자동화, 재고관리 개선, 드론 GCS 코드 분석·수정 경험
- **Linux 서버·네트워크 운영** — 해군 CERT에서 관제·장애 대응·점검 자동화 경험
- **SSAFY 16기 Java Track 교육 중** — Java·자료구조·알고리즘을 학습하며 개발 역량을 확장

## 프로젝트에서 사용한 기술

| 영역 | 기술 |
| --- | --- |
| AI·데이터 | Python · PyTorch · LoRA/Unsloth · YOLOv8 · Whisper · 검색 컨텍스트 구성 |
| 웹·API | FastAPI · Fastify · React · TypeScript · JavaScript |
| 데이터 저장·인증 | PostgreSQL · SQLite · Prisma · OAuth2 · JWT |
| 인프라·모니터링 | Linux · Docker · Kubernetes · Prometheus · Grafana |

## 다른 작업

[Python TCP 채팅](https://github.com/ho72/tcp-cli-chat) · [Dijkstra 시각화](https://github.com/ho72/dijkstra-visualizer)
