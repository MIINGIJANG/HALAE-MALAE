<div align="center">
  <img src="https://github.com/user-attachments/assets/2c24bb80-c5db-429c-abbe-eeb9955361eb" width="300" alt="할래말래 로고">
  <h1>🐆 할래말래 (Halae-Malae)</h1>
  <p><b>22212058 장민기 | [cite_start]Yeungnam University (컴퓨터공학과)</b> [cite: 2, 3, 4, 6]</p>
  <p><i>미니멀리즘 기반 대학생 맞춤형 D-Day 멘탈 케어 서비스</i></p>
</div>

<br/>

## [cite_start]📝 1. Business purpose [cite: 14]
* [cite_start]**프로젝트 배경**: 현재 대학생들의 학업 환경은 카카오톡(개인 일정), LMS(과제 일정), 학교 홈페이지(시험 일정) 등으로 데드라인 정보가 심각하게 파편화되어 있습니다[cite: 17]. [cite_start]통합 관리의 필요성은 절실하지만 막상 적합한 애플리케이션은 부재한 실정입니다[cite: 18].
* [cite_start]**기획 동기**: 기존의 '캘린더'나 '미리 알림' 앱은 단순히 정적인 표시와 텍스트 위주의 나열에 그쳐, 마감에 대한 직관적인 'D-Day' 압박감이나 실행 동기를 전혀 부여하지 못합니다[cite: 19, 20]. [cite_start]'벼락치기'의 악순환을 끊어낼 새로운 솔루션이 필요합니다[cite: 21].
* [cite_start]**최종 목표**: 여러 플랫폼에 흩어진 과제와 일정 정보를 단일화된 마감 리스트로 통합 관리하고, 'D-Day의 압박감'을 시각적으로 구현한 능동형 멘탈 케어 애플리케이션 **'할래말래'**를 설계 및 개발하는 것입니다[cite: 22]. [cite_start]시각적 피드백을 통해 행동을 유도하는 데 목적이 있습니다[cite: 23].
* [cite_start]**타겟 마켓**: 기존의 정적인 일정 앱에 만족하지 못해 할 일을 미루는 20대 대학생과 미니멀한 감성(Apple-style) 및 직관적인 D-Day 시각화 알림을 원하는 스마트폰 사용자입니다[cite: 24].

<br/>

## [cite_start]🏗️ 2. System context diagram [cite: 25]

<p align="center">
  <img src="https://github.com/user-attachments/assets/e87d2be5-5086-485f-a829-77e1bb607489" width="90%" alt="System Context Diagram">
</p>

* [cite_start]**할래말래 (Target App / System)**: 사용자가 직접 입력한 일정 데이터를 바탕으로 마감일(D-Day)을 계산하고, 푸시(PUSH) 알림을 발송하여 실행 동기를 부여하는 핵심 시스템입니다[cite: 48, 49].
* [cite_start]**사용자 (User / Primary Actor)**: 외부 환경에 파편화된 일정을 확인한 후 앱에 수동으로 입력하여 단일화하며, 통합 마감 리스트와 알림을 통해 멘탈 케어를 받는 주체입니다[cite: 45].
* [cite_start]**외부 정보 출처**: 사용자가 마감 일정 데이터를 획득하는 환경으로 카카오톡(비정형 개인/팀플 일정), LMS(과제 제출 일정), 학교 홈페이지(시험 일정)가 포함됩니다 (시스템과 자동 연동은 되지 않음)[cite: 43, 44].
* [cite_start]**기존 일정 관리 앱 (캘린더, 미리알림)**: 정적인 표시와 텍스트 나열에 그쳐 동기부여를 제공하지 못하므로, 능동적인 알림을 제공하는 '할래말래' 시스템으로 대체되어 사용이 중단(X 표시)되는 대상입니다[cite: 46, 47].

<br/>

## [cite_start]📌 3. Use case list [cite: 50]

| 유스케이스 명 | Actor | 상세 설명 |
| :--- | :--- | :--- |
| **1) 일정 직접 입력** | 사용자 | [cite_start]카카오톡, LMS, 홈페이지 등에서 확인한 개인 일정, 과제, 시험 등의 마감일과 내용을 앱에 직접 입력하여 등록한다[cite: 55, 56]. |
| **2) 통합 마감 리스트 조회** | 사용자 | [cite_start]등록된 일정을 마감일(D-Day)이 임박한 우선순위 순으로 정렬된 리스트 형태로 조회하여 출력한다[cite: 57, 58]. |
| **3) 통합 마감 캘린더 조회** | 사용자 | [cite_start]직접 입력한 모든 일정(개인, 과제, 시험) 데이터를 앱 내 통합 달력(Calendar) UI 위에서 한눈에 출력한다[cite: 59, 60]. |
| **4) 마감 임박 알람** | 사용자 | [cite_start]사용자가 설정한 마감 시간이 임박했을 때, 모바일 기기의 푸시 알림(Push Notification)을 통해 경고 알림을 수신한다[cite: 61, 62]. |
| **5) 일정 완료 처리** | 사용자 | [cite_start]해당 과제나 일정을 완수했을 경우, 체크하여 완료 상태로 변경하고 통합 리스트 및 달력에 반영한다[cite: 63, 64]. |

<br/>

## [cite_start]⚙️ 4. Concept of operation [cite: 66]

| 항목 | [cite_start]1) 일정 직접 입력 [cite: 69] | [cite_start]2) 통합 마감 리스트 조회 [cite: 71] | [cite_start]3) 통합 마감 캘린더 조회 [cite: 73] | [cite_start]4) 마감 임박 알람 [cite: 75] | [cite_start]5) 일정 완료 처리 [cite: 77] |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Purpose** | [cite_start]파편화된 일정 단일화 [cite: 70] | [cite_start]시급도 직관적 인지 [cite: 72] | [cite_start]일정 분포 시각적 파악 [cite: 74] | [cite_start]행동 유도 및 경각심 부여 [cite: 76] | [cite_start]완료일정 제외 및 성취감 부여 [cite: 79] |
| **Approach** | [cite_start]'추가' 버튼으로 제목/마감일시 입력 후 DB 기록 [cite: 70] | [cite_start]남은 시간(D-Day) 기준 가장 적은 순서대로 자동 정렬 출력 [cite: 72] | [cite_start]캘린더 UI 날짜에 데이터 매핑 및 하단 상세 표시 [cite: 74] | [cite_start]OS API를 호출해 사용자 기기 화면에 푸시 알림 발송 [cite: 76] | [cite_start]체크박스 탭/스와이프로 상태 업데이트 및 숨김 처리 [cite: 79] |
| **Goals** | [cite_start]산재된 데드라인 정보 통합 수동 입력 기능 구현 [cite: 70] | [cite_start]D-Day 기반 자동 정렬 리스트 뷰 기능 구현 [cite: 72] | [cite_start]통합 달력(Calendar) 상호작용 기능 구현 [cite: 74] | [cite_start]OS 연동 D-Day 타이머 및 푸시 알림 기능 구현 [cite: 76] | [cite_start]제스처 기반 상태 변경 및 UI 실시간 업데이트 구현 [cite: 79] |

<br/>

## [cite_start]⚠️ 5. Problem statement & NFRs [cite: 80]
* **문제점 및 기술적 난제**
    * [cite_start]**수동 입력에 따른 사용자 피로도 최소화**: 자동 연동을 배제하고 직접 입력 방식을 채택했으므로, 3단계 이내 터치로 완료되는 극도로 직관적이고 간편한 UI/UX 설계가 필수적입니다[cite: 83, 84].
    * [cite_start]**백그라운드 환경에서의 알림 정확성**: 모바일 OS의 엄격한 배터리 최적화 정책 속에서도 앱이 종료된 상태에서 알림 타이머가 죽지 않고 정확한 시점에 발송되도록 보장하는 기술 설계가 필요합니다[cite: 85, 86].
    * [cite_start]**시각적 자극과 피로감의 경계 유지**: 마감 임박에 대한 시각적 압박감이 과도한 불쾌감으로 이어지지 않도록 적절한 수준의 미니멀리즘과 심미성을 유지해야 합니다[cite: 87].
* [cite_start]**비기능 요구사항(NFRs)** [cite: 88]
    * [cite_start]**신뢰성(Reliability)**: 설정한 마감 기한 및 알림 시간에 오차나 지연 없이 100% 알림이 트리거되어야 합니다[cite: 89].
    * [cite_start]**사용성(Usability)**: 신규 일정 등록 시 3단계(Depth) 이내의 화면 전환만으로 입력이 완료되도록 구현해야 합니다[cite: 90].
    * [cite_start]**성능(Performance)**: 여러 일정이 등록된 상태에서도 리스트 뷰 및 달력 화면 간 전환 시 지연 현상(Lag) 없이 즉각적인 렌더링이 이루어져야 합니다[cite: 91].

<br/>

## [cite_start]📖 6. Glossary [cite: 93]
* [cite_start]**LMS (Learning Management System)**: 강의 수강 및 과제 제출 등을 관리하는 시스템으로, 마감일 정보가 발생하는 주요 외부 출처 중 하나입니다[cite: 96, 97].
* [cite_start]**파편화 (Fragmentation)**: 학업 및 개인 일정이 여러 플랫폼(홈페이지, LMS, 카카오톡 등)에 분산되어 통합 관리가 어려운 상태를 지칭합니다[cite: 98].
* [cite_start]**D-Day (디데이)**: 과제 마감일까지 남은 기한으로, 사용자에게 시급도를 전달하고 행동을 유도하는 핵심 연산 지표입니다[cite: 99].
* [cite_start]**UI 및 시각적 압박감**: 마감일이 다가옴에 따라 경각심과 실행 동기를 부여하는 본 애플리케이션의 핵심 디자인 원리입니다[cite: 100].
* [cite_start]**통합 일정 달력 (Integrated Calendar)**: 파편화된 일정을 수동으로 입력해 하나의 달력 화면에서 모아보고 시급도를 파악할 수 있는 기능입니다[cite: 101].
* [cite_start]**로컬 푸시 알림 (Local Push Notification)**: 외부 서버를 거치지 않고 기기 내부의 운영체제 스케줄링 기능을 활용해 경고 알림을 띄우는 방식입니다[cite: 102].

<br/>

## [cite_start]📚 7. References [cite: 103]
1. [cite_start]Alan Dennis, Barbara Haley Wixom and David Tegarden, *Systems Analysis and Design with UML: An Object-Oriented Approach*, 5th edition, Wiley. [cite: 106]
2. [cite_start]Grady Booch, James Rumbaugh, and Ivar Jacobson, *Unified Modeling Language User Guide*, 2nd Edition, Addison-Wesley Professional. [cite: 108]
3. [cite_start]Barrett Williams, *Open Source Collaboration: Harnessing the Power of Community for Software*. [cite: 110]
4. [cite_start]Apple Inc., *Human Interface Guidelines*. [cite: 112, 113, 114, 115, 116]

---
<div align="right">
  [cite_start]Copyright 2026. <b>장민기(mingijang@yu.ac.kr)</b> all rights reserved. [cite: 4, 5]
</div>
