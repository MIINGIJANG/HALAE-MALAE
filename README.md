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
