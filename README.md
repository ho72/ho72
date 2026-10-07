<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/header-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/header-light.svg">
  <img src="assets/header-light.svg" width="960" alt="ho72 — AI, Software, Systems">
</picture>

# 이호철

**AI를 서비스로 연결하고, 일상에 필요한 도구를 만듭니다.**

반려견 안구 질환을 분류·설명하는 VLM, Kubernetes 모니터링, 음성을 회의록으로 정리하는 도구를 개발했습니다. 모델의 입력과 출력을 개선하는 일부터 사용자가 결과를 확인하는 화면, 서비스 상태를 관찰하는 환경까지 관심을 두고 작업합니다.

생활 속 필요에서 출발한 개인 웹서비스도 만들고 있습니다. AI 코딩 도구와 함께 기획·설계·구현하고, 공통 인증과 서비스별 저장 구조를 연결해 개인 서버에서 운영합니다.

[프로젝트](#대표-프로젝트) · [개인 서비스](#직접-만들고-운영하는-서비스) · [기술](#사용한-기술) · [경험](#경험과-학습)

## 대표 프로젝트

### [01 · PET-I](https://github.com/ho72/pet-i-vlm-diagnosis)

<sub>반려견 안구 질환 분류·설명 VLM · 4인 졸업프로젝트</sub>

반려견 안구 사진에서 질환을 분류하고 증상을 설명하는 VLM 프로젝트입니다. AI Hub 이미지 데이터를 기반으로 모델 학습에 필요한 설명형 데이터를 만들고, 학습·평가를 반복하며 입력 구성과 응답 생성 문제를 개선했습니다.

**담당한 작업**

- **데이터·학습** — 설명형 데이터 생성·전처리와 Qwen3-VL-8B의 Unsloth·LoRA 학습 및 검증을 담당했습니다.
- **응답 생성 개선** — 문장이 반복되는 출력을 분석하고, EOS 토큰이 누락된 전처리를 보완해 응답이 정상적으로 끝나도록 수정했습니다.
- **이미지 입력 개선** — 안구만 잘라내면 눈물 자국과 주변 피부 정보가 사라지는 문제를 다뤘습니다. YOLO 탐지 영역에 여백을 둔 크롭과 학습 데이터 구성을 함께 개선했습니다.
- **검색 컨텍스트** — 문서와 웹 검색 결과에서 질문에 관련된 내용을 골라 모델 입력에 전달하는 흐름을 구현했습니다.

**평가와 수상**

- **평가** — 7개 분류·700장 기준 Macro F1 **0.6935 → 0.7404**, 최종 정확도 **74.00%**
- **팀 수상** — 건국대학교 2025학년도 생성형 AI 활용 사례 공모전 **우수상**

<sub>Python · PyTorch · Qwen3-VL-8B · Unsloth / LoRA · YOLOv8</sub>

[프로젝트 소개](https://github.com/ho72/pet-i-vlm-diagnosis) · [실험과 문제 해결](https://github.com/ho72/pet-i-vlm-diagnosis/blob/main/docs/DEVELOPMENT.md) · [데이터 생성 코드](https://github.com/ho72/pet-i-explanation-data)

### [02 · TacticAI Monitoring](https://github.com/ho72/tacticai-monitoring)

<sub>AI 대전 플랫폼의 Kubernetes 모니터링 · 4인 팀 프로젝트</sub>

턴제 보드게임의 AI 대전을 지원하는 분산 서버 프로젝트에서 **Prometheus Operator·Grafana 모니터링**을 담당했습니다. Gateway, AI Server, Game Server, 메시지 큐의 상태를 함께 보고, Pod가 늘어나도 수집 설정을 다시 고치지 않는 구조를 목표로 했습니다.

- **수집 구조** — ServiceMonitor·PodMonitor로 메트릭을 자동 수집하고, 서비스 로직 개발에 앞서 Mock-up 서버로 모니터링 흐름을 구성했습니다.
- **대시보드** — 요청량, 추론 지연, 매칭·대기열, 큐 적체를 서비스별로 살펴볼 수 있도록 지표를 구성했습니다.
- **확장 검증** — Mock-up 환경에서 AI Server Pod를 **3개 → 5개**로 확장하고, 설정 변경 없이 신규 Pod의 지표가 감지·표시되는 것을 확인했습니다.

<sub>Kubernetes · Prometheus · Grafana · Docker</sub>

[구현과 검증 화면](https://github.com/ho72/tacticai-monitoring) · [팀 프로젝트](https://github.com/KU-TacticAI)

### [03 · 회의록 생성기](https://github.com/ho72/meeting-notes-generator)

<sub>음성 업로드 → 전사·검토 → 회의록 생성·보관 · 개인 프로젝트</sub>

녹음 파일을 올린 뒤 전사문을 검토하고 회의록으로 정리하는 로컬 웹 도구입니다. Whisper로 음성을 전사하고 Gemini API로 회의록을 생성하며, 중간 결과를 사용자가 직접 확인·수정할 수 있도록 구성했습니다.

- **검토 흐름** — 전사문을 고친 뒤 생성하면 **수정한 내용이 회의록의 입력에 반영**됩니다. 생성된 회의록도 다시 편집·저장하고 Markdown으로 내려받을 수 있습니다.
- **작업·보관** — 음성 처리 대기열, 진행 상태, 실패 메시지를 제공하고, 저장한 프로젝트를 다시 열어 이전 결과를 확인할 수 있습니다.
- **유지보수** — API·음성 처리·저장·화면 코드를 분리하고, 중복 생성 요청과 저장·조회 흐름을 회귀 테스트로 점검할 수 있게 정리했습니다.

<sub>Python · FastAPI · faster-whisper · Gemini API · JavaScript</sub>

[기능과 실행 방법](https://github.com/ho72/meeting-notes-generator)

## 직접 만들고 운영하는 서비스

사진과 파일을 공유하고, 스마트홈 기기를 관리하고, 브라우저에서 AI 개발 작업을 이어가기 위해 만든 **1인 프로젝트**입니다. 기획과 기술 선택부터 화면·서버 구현까지 AI 코딩 도구와 함께 진행했습니다.

서비스가 늘어나면서 로그인 기능과 계정 관리를 각각 구현하는 일이 반복됐습니다. 이를 공통 인증 서버로 모으고, 각 서비스는 공통 사용자 ID를 기준으로 연결하되 자신의 데이터와 기능을 독립적으로 관리하도록 구성했습니다.

| 공개 코드 | 해결하는 일 |
| :--- | :--- |
| [공통 인증 서버](https://github.com/ho72/unified-auth-server) | Google·Kakao 로그인, 사용자 프로필, JWT 발급·갱신을 공통으로 관리 |
| [사진·파일 공유](https://github.com/ho72/home-media-sharing) | 앨범별 접근 권한, 사진·영상 업로드, 썸네일과 메타데이터 처리, 원본 다운로드 |
| [스마트홈 관리](https://github.com/ho72/smart-home-manager) | SmartThings·Xiaomi 기기 연동, 제어·자동화·알림을 한 화면에서 관리 |
| [AI 개발 워크스페이스](https://github.com/ho72/ai-coding-workspace) | Codex·Claude와 프로젝트별 대화, 자료 첨부, 생성 파일 확인·다운로드, 작업방 보관·복원 |

**개발·운영에서 다룬 문제**

- **인증 연동** — 공통 계정의 토큰·프로필을 각 서비스에서 확인하고 서비스별 사용자·세션에 연결했습니다.
- **미디어 응답** — 썸네일이 늦게 표시되는 원인을 살펴보고, 세션과 앨범 권한을 확인하는 엣지 캐시를 적용해 반복 요청의 원본 서버 접근을 줄였습니다.
- **작업의 연속성** — AI 개발 워크스페이스의 대화와 첨부파일을 서버에 보관해, 브라우저를 닫은 뒤에도 이전 작업을 이어갈 수 있도록 했습니다.

인증 서버와 서비스별 구조·실행 방법은 위 공개 레포에 정리했습니다.

## 사용한 기술

<p>
  <img src="assets/badges/python.svg" height="26" alt="Python">
  <img src="assets/badges/pytorch.svg" height="26" alt="PyTorch">
  <img src="assets/badges/fastapi.svg" height="26" alt="FastAPI">
  <img src="assets/badges/typescript.svg" height="26" alt="TypeScript">
  <img src="assets/badges/react.svg" height="26" alt="React">
  <img src="assets/badges/docker.svg" height="26" alt="Docker">
  <img src="assets/badges/kubernetes.svg" height="26" alt="Kubernetes">
  <img src="assets/badges/postgresql.svg" height="26" alt="PostgreSQL">
</p>

**AI·데이터** — LoRA / Unsloth · YOLOv8 · Whisper · 검색 컨텍스트

**웹·운영** — Fastify · Prisma · SQLite · OAuth2 / JWT · Linux · Prometheus / Grafana

## 경험과 학습

**소프트웨어 개발 실무**

AI를 활용한 문서 자동화, 재고관리 업무 개선, 드론 GCS 코드 분석·수정을 경험했습니다. 기존 코드와 업무 흐름을 이해한 뒤 필요한 기능을 보완하는 작업을 했습니다.

**해군 CERT**

Linux 서버와 네트워크 관제, 장애 대응 업무를 수행했습니다. 반복 점검을 스크립트로 자동화하고, 관제 화면에서 상태를 확인하기 위한 도구를 만들었습니다.

**교육**

건국대학교 컴퓨터공학부를 졸업했으며, 현재 **SSAFY 16기 Java Track**에서 교육을 받고 있습니다.

<details>
<summary>작은 프로젝트도 살펴보기</summary>

- [Python TCP 채팅](https://github.com/ho72/tcp-cli-chat) — 소켓·스레드 기반 터미널 채팅
- [Dijkstra 시각화](https://github.com/ho72/dijkstra-visualizer) — 최단 경로 알고리즘 시각화

</details>
