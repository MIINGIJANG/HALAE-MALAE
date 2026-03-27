<div align="center">
  <img src="https://github.com/user-attachments/assets/2c24bb80-c5db-429c-abbe-eeb9955361eb" width="300" alt="할래말래 로고">
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
* **프로젝트 배경**: 현재 대학생들의 학업 환경은 카카오톡(개인 일정), LMS(과제 일정), 학교 홈페이지(시험 일정) 등으로 데드라인 정보가 심각하게 파편화되어 있습니다. 통합 관리의 필요성은 절실하지만 막상 적합한 애플리케이션은 부재한 실정입니다.
* **기획 동기**: 기존의 '캘린더'나 '미리 알림' 앱은 단순히 정적인 표시와 텍스트 위주의 나열에 그쳐, 마감에 대한 직관적인 'D-Day' 압박감이나 실행 동기를 전혀 부여하지 못합니다. 
* **최종 목표**: 여러 플랫폼에 흩어진 과제와 일정 정보를 단일화된 마감 리스트로 통합 관리하고, 'D-Day의 압박감'을 시각적으로 구현한 능동형 멘탈 케어 애플리케이션 **'할래말래'**를 설계 및 개발하는 것입니다. 시각적 피드백을 통해 행동을 유도하는 데 목적이 있습니다.
* **타겟 마켓**: 기존의 정적인 일정 앱에 만족하지 못해 할 일을 미루는 20대 대학생과 미니멀한 감성(Apple-style) 및 직관적인 D-Day 시각화 알림을 원하는 스마트폰 사용자입니다.

<br/>

## 🏗️ 2. System context diagram

<p align="center">
  <img src="https://github.com/user-attachments/assets/e87d2be5-5086-485f-a829-77e1bb607489" width="90%" alt="System Context Diagram">
</p>

> 🖥️ **System & Actors Overview**

* **할래말래 (Target App / System)**: 사용자가 직접 입력한 일정 데이터를 바탕으로 마감일(D-Day)을 계산하고, 푸시(PUSH) 알림을 발송하여 실행 동기를 부여하는 핵심 시스템입니다.
* **사용자 (User / Primary Actor)**: 외부 환경에 파편화된 일정을 확인한 후 앱에 수동으로 입력하여 단일화하며, 통합 마감 리스트와 알림을 통해 멘탈 케어를 받는 주체입니다.
* **외부 정보 출처**: 사용자가 마감 일정 데이터를 획득하는 환경으로 카카오톡(비정형 개인/팀플 일정), LMS(과제 제출 일정), 학교 홈페이지(시험 일정)가 포함됩니다 (시스템과 자동 연동은 되지 않음).
* **기존 일정 관리 앱 (캘린더, 미리알림)**: 정적인 표시와 텍스트 나열에 그쳐 동기부여를 제공하지 못하므로, 능동적인 알림을 제공하는 '할래말래' 시스템으로 대체되어 사용이 중단(X 표시)되는 대상입니다.

<br/>

## 📌 3. Use case list

> 👤 **행위자(Actor) 정의**: 사용자(User) - 앱을 설치하고 실제 일정 관리 및 실행 동기 부여 서비스를 이용하는 사람.

#### 1) 일정 직접 입력
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 카카오톡, LMS, 학교 홈페이지 등에서 확인한 개인 일정, 과제, 시험 등의 마감일과 내용을 앱에 직접 입력하여 등록한다. |

#### 2) 통합 마감 리스트 조회
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 등록된 일정을 마감일(D-Day)이 임박한 우선순위 순으로 정렬된 리스트 형태로 조회하여 출력한다. |

#### 3) 통합 마감 캘린더 조회
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 직접 입력한 모든 일정(개인, 과제, 시험) 데이터를 앱 내 통합 달력(Calendar) UI 위에서 한눈에 출력한다. |

#### 4) 마감 임박 알람
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 설정한 마감 시간이 임박했을 때, 모바일 기기의 푸시 알림(Push Notification)을 통해 경고 알림을 수신한다. |

#### 5) 일정 완료 처리
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Actor** | 사용자 |
| **Description** | 사용자가 해당 과제나 일정을 완수했을 경우, 체크하여 완료 상태로 변경하고 통합 리스트 및 달력에 반영한다. |

<br/>

## ⚙️ 4. Concept of operation

#### 1) 일정 직접 입력
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Purpose** | 파편화된 마감 일정(LMS, 학교 홈페이지, 카카오톡 등)을 앱에 등록하여 단일화하기 위함 |
| **Approach** | 사용자가 앱 메인 화면에서 '추가(+)' 버튼을 눌러 일정의 제목, 카테고리, 마감 일시를 입력 후 저장하면 시스템이 데이터를 DB에 기록한다. |
| **Dynamics** | 새로운 과제나 일정을 인지하고 앱에 기록하려 할 때 발생 |
| **Goals** | 산재된 데드라인 정보를 통합하는 수동 입력 기능을 구현한다. |

#### 2) 통합 마감 리스트 조회
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Purpose** | 마감이 가장 임박한 순서대로 일정을 한눈에 파악하여 시급도를 직관적으로 인지하기 위함 |
| **Approach** | 사용자가 앱 메인 리스트 화면에 접속하면, 시스템이 DB에 등록된 일정을 현재 시간 기준으로 남은 시간이 가장 적은 순서대로 자동 정렬하여 화면에 출력한다. |
| **Dynamics** | 앱을 실행하여 현재 가장 시급하게 처리해야 할 일이 무엇인지 확인할 때 발생 |
| **Goals** | 남은 시간(D-Day) 기반의 자동 정렬 리스트 뷰(List View) 기능을 구현한다. |

#### 3) 통합 마감 캘린더 조회
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Purpose** | 사용자가 입력한 모든 데드라인을 전체적인 월간 달력 위에서 시각적으로 파악하기 위함 |
| **Approach** | 사용자가 캘린더 탭을 누르면, 시스템이 등록된 전체 일정 데이터를 캘린더 UI의 해당 날짜에 매핑하여 표시하며, 날짜 클릭 시 하단에 상세 마감일 리스트가 노출된다. |
| **Dynamics** | 전체적인 이번 달이나 이번 주의 일정 분포와 몰림 정도를 시각적으로 점검할 때 발생 |
| **Goals** | 등록된 데이터를 바탕으로 통합 달력(Calendar) UI 상호작용 기능을 구현한다. |

#### 4) 마감 임박 알람
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Purpose** | 앱을 켜지 않은 상태에서도 다가오는 마감일을 인지하여 사용자의 행동을 유도하기 위함 |
| **Approach** | 시스템이 백그라운드에서 현재 시간과 마감 일시를 비교 연산하여, 특정 조건 도달 시 모바일 OS의 API를 호출해 사용자 기기 화면에 푸시 알림을 발송한다. |
| **Dynamics** | 등록해 둔 일정의 마감 시간이 임박했을 때 시스템에 의해 자동으로 트리거됨 |
| **Goals** | OS 연동을 통한 D-Day 기반 타이머 및 푸시 알림(Push) 기능을 구현한다. |

#### 5) 일정 완료 처리
| 구분&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 내용 |
| :--- | :--- |
| **Purpose** | 완료한 일정을 리스트에서 제외하여 성취감을 부여하고 헷갈리지 않게 관리하기 위함 |
| **Approach** | 사용자가 특정 일정의 체크박스를 탭하거나 스와이프 하면, 시스템이 데이터의 상태를 '완료'로 업데이트하고 진행 중인 리스트에서 숨김 처리를 한다. |
| **Dynamics** | 과제 제출, 시험 응시 등 해당 목표를 실제로 완수한 직후 발생 |
| **Goals** | 사용자 제스처 기반의 데이터 상태 변경 및 UI 실시간 업데이트 기능을 구현한다. |

<br/>

## ⚠️ 5. Problem statement & NFRs

> 🚧 **문제점 및 기술적 난제**
> 1. **수동 입력에 따른 사용자 피로도 최소화**: 외부 시스템과의 자동 데이터 연동을 배제하고 사용자의 직접 입력(Manual Input) 방식을 채택했으므로 극도로 직관적이고 간편한 UI/UX 설계가 필수적입니다.
> 2. **백그라운드 환경에서의 알림 정확성**: 모바일 OS의 엄격한 배터리 최적화 정책 속에서도 앱이 종료된 상태에서 알림 타이머가 죽지 않고 정확히 발송되도록 보장하는 기술적 설계가 필요합니다.
> 3. **시각적 자극과 피로감의 경계 유지**: 마감이 다가올수록 '시각적 압박감'을 주는 것이 핵심이지만, 이것이 과도한 시각적 피로도나 불쾌감으로 이어지지 않도록 적절한 수준의 미니멀리즘을 유지해야 합니다.

* **비기능 요구사항(NFRs)**
    * **신뢰성(Reliability)**: 설정한 마감 기한 및 알림 설정 시간에 오차나 지연 없이 100% 알림이 트리거되어야 합니다.
    * **사용성(Usability)**: 신규 일정 등록 시 3단계(Depth) 이내의 화면 전환만으로 입력이 완료되도록 직관적인 UI를 구현해야 합니다.
    * **성능(Performance)**: 여러 일정이 등록된 상태에서도 리스트 뷰 및 통합 달력 화면 간 전환 시 지연 현상(Lag) 없이 즉각적인 렌더링이 이루어져야 합니다.

<br/>

## 📖 6. Glossary

| 용어 | 상세 설명 |
| :--- | :--- |
| **LMS** | 대학에서 학생들의 온라인 강의 수강, 과제 제출, 성적 확인 등을 온라인으로 지원하고 관리하는 '학습관리시스템'을 의미합니다. |
| **파편화** | 대학생의 학업 및 개인 일정(과제, 팀 프로젝트, 시험 등)이 학교 홈페이지, LMS, 메신저 등 여러 플랫폼에 분산되어 관리하기 어려운 상태를 지칭합니다. |
| **D-Day** | 특정 과제나 일정의 마감일(Deadline)까지 남은 기한을 의미하며, 사용자에게 일정의 시급도를 전달하고 행동을 유도하는 핵심 연산 지표입니다. |
| **시각적 압박감** | 마감일(D-Day)이 다가옴에 따라 사용자에게 경각심과 실행 동기를 부여하는 본 애플리케이션의 핵심 디자인 원리입니다. |
| **통합 일정 달력** | 파편화된 다양한 목적의 일정을 수동으로 입력하여 하나의 달력(Calendar) 화면 위에서 종합적으로 모아보고 시급도를 파악할 수 있도록 구현한 기능입니다. |
| **로컬 푸시 알림** | 외부 통신 서버를 거치지 않고 사용자 기기 내부의 운영체제(iOS/Android) 스케줄링 기능을 활용하여, 지정된 마감 임박 시간에 경고 알림을 띄우는 방식입니다. |

<br/>

## 📚 7. References
1. Alan Dennis, Barbara Haley Wixom and David Tegarden, *Systems Analysis and Design with UML: An Object-Oriented Approach*, 5th edition, Wiley.
2. Grady Booch, James Rumbaugh, and Ivar Jacobson, *Unified Modeling Language User Guide*, 2nd Edition, Addison-Wesley Professional.
3. Barrett Williams, *Open Source Collaboration: Harnessing the Power of Community for Software*.
4. Apple Inc., *Human Interface Guidelines*.

---
<div align="right">
  Copyright 2026. <b>장민기(mingijang@yu.ac.kr)</b> all rights reserved.
</div>
