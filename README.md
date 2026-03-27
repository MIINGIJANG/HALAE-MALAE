<div align="center">
  <img src="https://github.com/user-attachments/assets/2c24bb80-c5db-429c-abbe-eeb9955361eb" width="300" alt="Halae-Malae Logo">
  <h1>🐆 할래말래 (Halae-Malae)</h1>
  <p><i>"미니멀리즘 기반 대학생 맞춤형 D-Day 멘탈 케어 서비스"</i></p>
</div>

<br/>

### 📌 Project Properties
| Property | Description |
| :--- | :--- |
| **Author** | 22212058 장민기 |
| **Affiliation** | 영남대학교 컴퓨터공학과 (Yeungnam University) |
| **Contact** | mingijang@yu.ac.kr |
| **Date** | 2026-03-27 |

---

> 💡 **Core Value**
> 파편화된 대학생의 일정을 단일화하고, 시각적 압박감을 통해 실질적인 실행 동기를 부여하여 '벼락치기'의 악순환을 끊어내는 능동형 멘탈 케어 솔루션입니다.

<br/>

## 📝 1. Business purpose

### 1.1. 프로젝트 배경 (Project Background)
현재 대학생들의 학업 및 캠퍼스 라이프 환경은 정보의 홍수 속에 있으며, 특히 중요 일정(데드라인) 정보가 심각하게 파편화되어 있습니다. 통합 관리의 필요성은 절실하지만 막상 적합한 애플리케이션은 부재한 실정입니다.
* **개인 일정**: 카카오톡 등 사적 메신저를 통해 유입.
* **과제 및 학업 일정**: 대학 자체 학습관리시스템(LMS)을 통해 고지.
* **시험 및 주요 학사 일정**: 학교 공식 홈페이지를 통해 공지.

### 1.2. 기획 동기 (Motivation)
기존 시장에 존재하는 '캘린더'나 '미리 알림' 애플리케이션은 단순히 일정을 정적으로 표시하거나 텍스트를 나열하는 수준에 그칩니다. 이러한 방식은 사용자에게 마감 임박에 대한 심리적 압박감을 직관적으로 전달하지 못하며, 결과적으로 실질적인 행동을 유도하는 실행 동기를 부여하는 데 한계가 있습니다.

### 1.3. 최종 목표 (Final Goal)
본 프로젝트의 최종 목표는 파편화된 데드라인 정보를 단일 시스템으로 통합하고, 단순한 정보 제공을 넘어 사용자가 마감 기한을 직관적으로 인지할 수 있도록 'D-Day의 압박감'을 시각적으로 구현하는 것입니다. 이를 통해 사용자의 행동 변화를 유도하는 능동형 멘탈 케어 애플리케이션 **'할래말래'**를 개발하고자 합니다.

### 1.4. 타겟 마켓 (Target Market)
* **주 타겟**: 기존의 정적인 일정 관리 앱에 만족하지 못해 할 일을 미루는 20대 대학생.
* **부 타겟**: 미니멀한 감성(Apple-style)의 UI/UX와 직관적인 D-Day 시각화를 선호하는 스마트폰 사용자 전체.

<br/>

## 🏗️ 2. System context diagram

<p align="center">
  <img src="https://github.com/user-attachments/assets/b3eec587-fa35-4575-b163-013aee1ffe48" width="90%" alt="System Context Diagram">
</p>

> 🖥️ **System & Actors Overview**

* **할래말래 (Target App / System)**: 사용자가 직접 입력한 일정 데이터를 바탕으로 마감일(D-Day)을 계산하고, 가변적 UI와 푸시 알림(Push Notification)을 통해 사용자의 행동을 유도하는 핵심 시스템입니다.
* **사용자 (User / Primary Actor)**: 파편화된 외부 정보를 확인하여 시스템에 직접 입력하고, 통합된 마감 리스트와 알림을 통해 일정 및 멘탈 관리를 받는 주체입니다.
* **외부 정보 출처**: 사용자가 마감 일정 데이터를 획득하는 환경으로 카카오톡(비정형 개인 일정), LMS(과제 일정), 학교 홈페이지(시험 일정) 등이 포함됩니다.
* **기존 일정 관리 앱 (캘린더, 미리알림 등)**: 사용자가 기존에 사용하던 정적 앱으로, 본 시스템 도입 시 사용이 중단되는 대상입니다 (X 표시).

<br/>

## 📌 3. Use case list

> 👤 **행위자(Actor) 정의**: 사용자(User) - 앱을 설치하고 실제 일정 관리 및 실행 동기 부여 서비스를 이용하는 사람.

#### 3.1. 일정 직접 입력 (ID: UC-01)
| 구분 | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 카카오톡, LMS, 학교 홈페이지 등에서 확인한 개인 일정, 과제, 시험 등의 마감일과 내용을 앱에 직접 입력하여 등록한다. |

#### 3.2. 통합 마감 리스트 조회 (ID: UC-02)
| 구분 | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 등록된 일정을 마감일(D-Day)이 임박한 우선순위 순으로 정렬된 리스트 형태로 조회하여 출력한다. |

#### 3.3. 통합 마감 캘린더 조회 (ID: UC-03)
| 구분 | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 직접 입력한 모든 일정 데이터를 앱 내 통합 달력(Calendar) UI 위에서 한눈에 출력한다. |

#### 3.4. 마감 임박 알람 수신 (ID: UC-04)
| 구분 | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 설정한 마감 시간이 임박했을 때, 모바일 기기의 푸시 알림(Push Notification)을 통해 경고 알림을 수신한다. |

#### 3.5. 일정 완료 처리 (ID: UC-05)
| 구분 | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 해당 과제나 일정을 완수했을 경우, 체크하여 완료 상태로 변경하고 통합 리스트 및 달력에 반영한다. |

<br/>

## ⚙️ 4. Concept of operation (운영 개념)

#### 4.1. 일정 직접 입력 (Conceptual Dynamics)
| 구분 | 내용 |
| :--- | :--- |
| **Dynamics** | 새로운 일정 인지 시 발생 |
| **Approach** | 추가 버튼 클릭 -> 카테고리/제목/마감일시 입력 -> 저장 클릭 |
| **Goals** | 산재된 데드라인 정보 단일화 |

#### 4.2. 통합 마감 리스트 조회 (Conceptual Dynamics)
| 구분 | 내용 |
| :--- | :--- |
| **Dynamics** | 앱 실행 시 자동 발생 |
| **Approach** | 앱 실행 -> D-Day 기반 자동 정렬 리스트 출력 |
| **Goals** | 시급도 직관적 인지 및 벼락치기 악순환 방지 |

#### 4.3. 통합 마감 캘린더 조회 (Conceptual Dynamics)
| 구분 | 내용 |
| :--- | :--- |
| **Dynamics** | 전체적인 일정 분포 파악 시 발생 |
| **Approach** | 캘린더 탭 클릭 -> 달력 날짜에 마감일 매핑 표시 |
| **Goals** | 일정 분포의 시각적 파악 및 사전 계획 수립 유도 |

#### 4.4. 마감 임박 알람 수신 (Conceptual Dynamics)
| 구분 | 내용 |
| :--- | :--- |
| **Dynamics** | 특정 마감 임박 조건 도달 시 자동 트리거 |
| **Approach** | 백그라운드 연산 -> D-24h / D-1h 등 푸시 알림 수신 |
| **Goals** | 능동적 실행 동기 부여 |

#### 4.5. 일정 완료 처리 (Conceptual Dynamics)
| 구분 | 내용 |
| :--- | :--- |
| **Dynamics** | 과제 완수 직후 발생 |
| **Approach** | 완료 체크박스 탭/스와이프 -> 상태 업데이트 및 취소선/숨김 처리 |
| **Goals** | 성취감 부여 및 완료 일정 관리 |

<br/>

## ⚠️ 5. Problem statement & NFRs

> 🚧 **문제점 및 기술적 난제**
> 1. **수동 입력 피로도 최소화 UI 설계**: 직접 입력 방식을 채택했으므로, 3단계(Depth) 이내 터치로 완료되는 직관적인 UI 설계가 필수적입니다.
> 2. **백그라운드 알림 정확성 확보**: 앱이 종료된 상태에서도 타이머가 정확히 작동하여 알림이 발송되도록 기술적 설계가 필요합니다.
> 3. **시각적 압박감과 심미성의 조화**: 경각심을 주는 시각적 압박감이 미니멀한 감성을 해치지 않도록 균형을 잡아야 합니다.

* **비기능 요구사항(NFRs)**
    * **신뢰성(Reliability)**: 설정한 알림 시간에 오차 없이 100% 트리거되어야 함.
    * **사용성(Usability)**: 신규 일정 등록 시 3단계 이내로 완료되는 UI 제공.
    * **성능(Performance)**: 화면 전환 시 지연 없는 즉각적인 렌더링 보장.

<br/>

## 📖 6. Glossary

* **LMS (Learning Management System)**: 대학 학습관리시스템으로, 마감 정보의 주요 출처 중 하나입니다 Std No_Name-2.pdf].
* **파편화 (Fragmentation)**: 일정이 여러 플랫폼에 분산되어 관리가 어려운 상태를 뜻합니다 Std No_Name-2.pdf].
* **D-Day**: 과제 마감일까지 남은 기한으로, 시급도를 전달하는 핵심 지표입니다 Std No_Name-2.pdf].
* **가변적 UI**: 마감 임박도에 따라 테마나 마스코트가 변화하는 설계 원리입니다 Std No_Name-2.pdf].
* **로컬 푸시 알림**: 외부 서버 없이 기기 내부 기능을 활용해 알림을 띄우는 방식입니다 Std No_Name-2.pdf].

<br/>

## 📚 7. References
1. Alan Dennis et al., *Systems Analysis and Design with UML*, 5th edition, Wiley.
2. Grady Booch et al., *Unified Modeling Language User Guide*, 2nd Edition.
3. Barrett Williams, *Open Source Collaboration*.
4. Apple Inc., *Human Interface Guidelines*.

---
<div align="right">
  Copyright 2026. <b>장민기(mingijang@yu.ac.kr)</b> all rights reserved.
</div>
