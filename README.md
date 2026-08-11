<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a936f,100:88d498&height=170&section=header&text=minjoo%20kim&fontSize=46&fontColor=ffffff&fontAlignY=36&desc=Build%20it%20-%20Ship%20it%20-%20Run%20it&descSize=16&descAlignY=58" width="100%" />

### 앱을 화면부터 서버까지 만들고, 스토어에 올려 운영합니다

React Native로 만든 앱을 실제 스토어에서 서비스하고 있고,<br />
Spring Boot 기반 MSA에서 결제와 동시성 문제를 다룹니다.

<br />

![Java](https://img.shields.io/badge/Java_21-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JPA](https://img.shields.io/badge/JPA_·_QueryDSL-59666C?style=flat-square&logo=hibernate&logoColor=white)

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React Native](https://img.shields.io/badge/React_Native-61DAFB?style=flat-square&logo=react&logoColor=black)
![Expo](https://img.shields.io/badge/Expo-000020?style=flat-square&logo=expo&logoColor=white)
![Zustand](https://img.shields.io/badge/Zustand-433E38?style=flat-square&logo=react&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white)

![AWS](https://img.shields.io/badge/AWS_EC2-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat-square&logo=figma&logoColor=white)

</div>

---

## 이런 걸 해왔습니다

- **출시하고 운영해봤습니다.** 스토어 심사 반려 대응, 구독 결제 연동, 사용자 행동 계측과 노출 실험까지 — 만드는 것과 서비스하는 것의 차이를 겪었습니다.
- **돈이 오가는 코드를 다룹니다.** 앱에서는 인앱 구독을, 서버에서는 PG 연동과 분산 트랜잭션을 맡았습니다. "결제는 됐는데 물건이 없는" 상황을 막는 일을 해왔습니다.
- **혼자서도 끝까지 갑니다.** 개인 프로젝트에서는 기획·디자인·앱·서버·인프라를 전부 직접 했습니다.

---

## 진행 중인 프로젝트

### 🌳 영어의 숲 — AI 영어 일기 학습 앱

`iOS · Android 출시 운영 중 (v1.6.1)` &nbsp;|&nbsp; **React Native · TypeScript · Expo Router · Zustand**

영어 일기를 쓰면 AI가 꼬리질문을 던지고, 거기서 뽑은 단어를 복습하게 하는 학습 앱입니다.
클라이언트 개발을 맡아 기능 개발부터 스토어 출시·운영까지 담당하고 있습니다.

- **구독 결제 · 페이월** — RevenueCat 기반 인앱 구독, 플랜 개편과 마일스톤 오퍼 설계, 배너 노출 실험
- **그로스 계측** — Mixpanel · Firebase Analytics · AppsFlyer · Microsoft Clarity로 퍼널 이벤트를 설계하고, Sentry로 릴리스별 오류를 추적
- **출시 운영** — iOS 심사 반려 대응(권한 문구 정비), 격주 배포 사이클, QA 회차 반영
- **핵심 기능** — STT 기반 말하기 학습, 소셜 로그인(카카오·구글·애플), 공유 일기와 SNS 공유 카드

> 비공개 저장소라 코드는 공개되어 있지 않습니다. 상세 구현은 요청 시 설명드릴 수 있습니다.

<br />

### 🎫 TicketRush — 대규모 트래픽 티켓 예매 플랫폼

`진행 중` &nbsp;|&nbsp; **Java 21 · Spring Boot · Spring Cloud · Kafka · Redis · MySQL**

인기 공연 티켓 오픈처럼 짧은 시간에 트래픽이 몰리는 환경을 다루는 백엔드입니다.
8개 서비스로 나눈 MSA 구조에서 **공연 · 결제 도메인과 CI, 디자인**을 맡았습니다.

- **결제 정합성** — 결제 확정 시 예매 소유자를 대조해 *남의 예매에 결제가 귀속되던 결함*을 차단
- **보상 트랜잭션** — 좌석 확정 실패 시 자동 환불되도록 Saga 보상 흐름을 구성해, 과금됐는데 좌석이 없는 상태를 제거
- **PG 예외 분류** — Toss Payments 취소 실패를 원본 에러 코드로 분류해, 일시적 거절은 재시도로 흡수하고 영구 실패만 알림
- **쿼리 최적화** — 결제 내역 조회의 전수 스캔을 `(user_id, status)` 복합 인덱스로 제거
- **동시성 방어** — `@DynamicUpdate`로 공연 엔티티의 stale 덮어쓰기 차단

🔗 [TicketRush/TicketRush-backend](https://github.com/TicketRush/TicketRush-backend)

<br />

### 📸 offmode — 오프라인 미션 습관 형성 앱

`개인 프로젝트` &nbsp;|&nbsp; **React Native · Expo · Spring Boot · MySQL · AWS**

매일 하나의 오프라인 미션을 사진으로 인증하는 소셜 챌린지 앱입니다.
**앱 · 서버 · 인프라 · 디자인을 혼자 전부** 담당했습니다.

- 방(Room) 기반 미션 구조와 멤버 간 상호 인증(피어 확인) 설계
- Spring Boot + JPA 백엔드, Flyway 마이그레이션(H2/MySQL 이중 관리), JWT 인증
- AWS EC2 + RDS + Nginx + Let's Encrypt HTTPS 직접 구축, 태그 기반 자동 배포
- EAS Build로 iOS 빌드·스토어 제출, 이미지 저장은 Cloudflare R2

🔗 [OffmodePub/offmode](https://github.com/OffmodePub/offmode)

---

## 개발 활동

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com/?user=calla1102&theme=dark&hide_border=true&background=00000000&date_format=Y/n/j&ring=1a936f&fire=1a936f&currStreakLabel=88d498" />
  <img src="https://streak-stats.demolab.com/?user=calla1102&hide_border=true&background=00000000&date_format=Y/n/j&ring=1a936f&fire=1a936f&currStreakLabel=1a936f" width="100%" />
</picture>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-activity-graph.vercel.app/graph?username=calla1102&theme=github-dark&hide_border=true&bg_color=00000000&color=88d498&line=1a936f&point=88d498&area=true&area_color=1a936f" />
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=calla1102&theme=github-compact&hide_border=true&bg_color=00000000&color=1a936f&line=1a936f&point=1a936f&area=true&area_color=88d498" width="100%" />
</picture>

</div>

---

## 이전 프로젝트

### 💸 0끌 — 커뮤니티 기반 게이미피케이션 지출 관리 앱

`팀 프로젝트 (5인)` &nbsp;|&nbsp; **Kotlin 2.0 · Android · Spring**

"어떻게 하면 좀 더 재미있게 돈을 절약할 수 있을까?"에서 출발한 무지출 챌린지 앱입니다.
절약에 성공하면 리워드를 받아 캐릭터를 꾸미고, 챌린저들과 절약 점수 랭킹으로 경쟁합니다.

- **상점 · 리워드 획득** 기능을 담당해 절약 성공 → 리워드 지급 → 캐릭터 꾸미기로 이어지는 보상 루프를 구현
- 안드로이드 네이티브(Kotlin) 환경에서 팀 5인과 도메인을 나눠 개발

🔗 [yeongkkeul/yeongkkuel-android](https://github.com/calla1102/yeongkkuel-android)

<br />

### 🌿 숲결 — 친환경 습관 형성 앱

`구름톤 서북지구 · B4AFTER 팀` &nbsp;|&nbsp; **React Native · Expo · TypeScript**

일상 속 친환경 실천을 기록하면 나무가 자라는 습관 형성 앱입니다.
**팀에서 유일한 프론트엔드**로 앱 전체 화면을 혼자 구현했습니다 (나머지 4명은 백엔드).

- `씨앗 → 새싹 → 작은 나무 → 나무` 성장 단계 시각화와 캘린더 기반 실천 기록
- 상점 · 인벤토리 · 리워드 게이미피케이션 구조, 소셜 로그인 연동
- 백엔드 4명이 내려주는 API를 혼자 받아내야 해서, **Swagger·Notion 명세를 대조해 불일치를 찾아내고 백엔드와 직접 조율**
- 응답이 불안정한 호출 구간은 헬퍼 함수로 모듈화해 오류 처리를 한곳으로 모음

🔗 [숲결 Frontend](https://github.com/calla1102/Frontend)

<br />

### 📊 파이낸스닥 — 청년 대상 AI 재무 관리·금융 상품 추천 앱

`개방형 클라우드 플랫폼(K-PaaS) 활용 공모전` &nbsp;|&nbsp; **React Native · Expo Router · TypeScript**

청년의 재무 상태를 진단하고 맞춤 금융 상품과 금융 교육 콘텐츠를 추천하는 앱입니다.
프론트엔드를 담당했으며, 백엔드는 K-PaaS 위에 올린 MSA(회원·리포트·추천·교육 서비스 + 상품 크롤러)로 구성됐습니다.

- 여러 마이크로서비스로 분리된 API를 게이트웨이 경유로 연동
- 재무 리포트·상품 추천 결과를 모바일 화면으로 시각화

🔗 [Finance-doc/Frontend](https://github.com/Finance-doc/Frontend)

---

<div align="center">

### Contact

📧 **calla20031@naver.com**

🔍 **관심 분야** — 실서비스 운영 · 결제 도메인 · 대규모 트래픽 · 프로덕트 디자인

</div>
