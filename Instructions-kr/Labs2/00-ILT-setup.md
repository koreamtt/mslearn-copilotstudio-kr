---
---

# LAB 00. Power Platform 환경 만들기

## 개요

이 실습에서는 실습에 필요한 Power Platform 환경을 만듭니다.

## TASK 01. Power Platform 환경 만들기

1. 브라우저를 열고 [https://admin.powerplatform.com](https://admin.powerplatform.com) 사이트에 실습 환경에서 제공하는 계정과 암호를 사용하여 액세스합니다.

2. 기본 환경에 Dataverse를 추가해야 합니다. `관리 > 환경`으로 이동한 후 `Contoso(기본)` 환경을 선택하고 `… > Dataverse 추가`를 클릭합니다.

   ![Power Platform 관리 센터에서 Contoso(기본) 환경을 선택하고 Dataverse 추가 메뉴를 여는 위치](./images/00-ILT-setup/exercise-00-task-01-step-02-default-environment-add-dataverse.png)

3. `Dataverse 추가` 창에서 다음과 같이 구성한 후 `추가`를 클릭합니다.

   | 항목 | 값 |
   |---|---|
   | `언어` | `한국어(대한민국)` |
   | `통화` | `KRW (₩)` |
   | `샘플 앱 및 데이터를 배포하시겠어요` | `아니요` |

   ![기본 환경의 Dataverse 추가 창에서 한국어, KRW 통화 및 샘플 앱과 데이터 배포 안 함을 설정한 상태](./images/00-ILT-setup/exercise-00-task-01-step-03-default-environment-dataverse-settings.png)

4. 실습에서 사용할 새 환경을 만들기 위해 `관리 > 환경`의 메뉴에서 `+ 새로 만들기`를 클릭합니다.

   ![Power Platform 관리 센터의 환경 페이지에서 새 환경을 만드는 새로 만들기 버튼 위치](./images/00-ILT-setup/exercise-00-task-01-step-04-new-environment-menu.png)

5. `새 환경` 창에서 다음과 같이 구성한 후 `다음`을 클릭합니다.

   | 항목 | 값 |
   |---|---|
   | `유형` | `개발자` |
   | `매크로 지역 지리` | `아시아 태평양` |
   | `이름` | `CopilotLabEnv` |
   | `기본 설정 변경 > 환경 그룹` | `없음` |
   | `기본 설정 변경 > 관리형 환경으로 설정` | `아니요` |
   | `기본 설정 변경 > 대신 만들기` | `아니요` |
   | `기본 설정 변경 > Dataverse 데이터 저장소를 추가하시겠습니까` | `예` |
   | `기본 설정 변경 > Azure 종량제를 이용하시겠습니까` | `아니요` |

   ![새 환경 창에서 CopilotLabEnv의 개발자 유형, 아시아 태평양 지역 및 Dataverse 사용 등 기본 설정을 구성한 상태](./images/00-ILT-setup/exercise-00-task-01-step-05-developer-environment-settings.png)

6. `Dataverse 추가` 창에서 다음과 같이 구성한 후 `저장`을 클릭합니다.

   | 항목 | 값 |
   |---|---|
   | `언어` | `한국어(대한민국)` |
   | `통화` | `KRW (₩)` |
   | `샘플 앱 및 데이터를 배포하시겠어요` | `아니요` |

   ![새 개발자 환경의 Dataverse 추가 창에서 한국어, KRW 통화 및 샘플 앱과 데이터 배포 안 함을 설정한 상태](./images/00-ILT-setup/exercise-00-task-01-step-06-developer-environment-dataverse-settings.png)

7. `관리 > 환경` 페이지의 메뉴에서 `새로 고침`을 클릭하여 새로 만든 환경이 `준비` 상태로 표시될 때까지 기다립니다.

   > [!NOTE]
   > 환경이 `준비` 상태로 표시될 때까지 몇 분이 걸릴 수 있습니다.

   ![Power Platform 관리 센터의 환경 목록에서 CopilotLabEnv가 준비 상태로 표시된 결과](./images/00-ILT-setup/exercise-00-task-01-step-07-environment-ready.png)

## TASK 02. Copilot Studio의 표준 하네스 시작하기

1. 브라우저에서 새 탭을 열고 [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com) 사이트로 이동합니다.

2. 새로운 Copilot Studio 환경이 표시되면 왼쪽 아래의 환경을 클릭한 후 `CopilotLabEnv` 환경을 선택합니다.

   ![Copilot Studio 왼쪽 아래의 환경 전환 메뉴에서 CopilotLabEnv 환경을 선택하는 위치](./images/00-ILT-setup/exercise-00-task-02-step-02-copilot-studio-select-environment.png)

3. 왼쪽 하단의 계정 우측에서 `… > 클래식 환경 열기`를 클릭합니다. 피드백 창이 표시되면 `피드백 건너뛰기`를 클릭합니다.

   ![Copilot Studio의 계정 우측 더 보기 메뉴에서 클래식 환경 열기를 선택하는 위치](./images/00-ILT-setup/exercise-00-task-02-step-03-copilot-studio-open-classic.png)

## TASK 03. 솔루션 만들기

1. Copilot Studio의 클래식 포털에서 새로운 솔루션을 만들어야 합니다. 왼쪽 내비게이션 메뉴에서 `… > 솔루션`을 클릭합니다.

   ![Copilot Studio 클래식 포털의 왼쪽 내비게이션 더 보기 메뉴에서 솔루션을 선택하는 위치](./images/00-ILT-setup/exercise-00-task-03-step-01-classic-portal-solutions-menu.png)

2. `솔루션` 페이지의 메뉴에서 `+ 새 솔루션`을 클릭합니다.

   ![Copilot Studio 솔루션 페이지의 새 솔루션 버튼 위치](./images/00-ILT-setup/exercise-00-task-03-step-02-new-solution-menu.png)

3. `새 솔루션` 창에서 다음과 같이 구성합니다.

   | 항목 | 값 또는 작업 |
   |---|---|
   | `표시 이름` | `LabSolution` |
   | `이름` | `LabSolution` |
   | `게시자` | `+ 새 게시자`를 클릭합니다. |

   ![새 솔루션 창에서 표시 이름과 이름에 LabSolution을 입력하고 새 게시자를 만드는 위치](./images/00-ILT-setup/exercise-00-task-03-step-03-solution-details-new-publisher.png)

4. `새 게시자` 창의 `속성` 탭에서 다음과 같이 구성하고 `저장`을 클릭합니다.

   | 항목 | 값 |
   |---|---|
   | `표시 이름` | `Fabrikam` |
   | `이름` | `fabrikam` |
   | `접두사` | `fab` |
   | `선택 값 접두사` | 기본값을 사용합니다. |

   ![새 게시자의 속성 탭에서 표시 이름 Fabrikam, 이름 fabrikam, 접두사 fab 및 기본 선택 값 접두사를 구성한 상태](./images/00-ILT-setup/exercise-00-task-03-step-04-publisher-properties.png)

5. `새 솔루션` 창이 다시 표시되면 `게시자`에 앞서 만들었던 `Fabrikam (fabrikam)` 게시자를 선택하고 `선호하는 솔루션으로 설정` 옵션을 선택한 후 `만들기`를 클릭합니다.

   ![새 솔루션 창에서 Fabrikam 게시자를 선택하고 선호하는 솔루션으로 설정 옵션을 선택한 상태](./images/00-ILT-setup/exercise-00-task-03-step-05-preferred-solution-create.png)

## 문서 정보

- 과정: `PL-7008` — Create agents in Microsoft Copilot Studio
- 기관 및 프로그램: 한국 마이크로소프트 · Microsoft Technical Trainer · Enterprise Skills Initiative
- 표지 표기: Worldwide Learning | Microsoft Technical Trainer

### 문서 작성 연혁

| 날짜 | 버전 | 작성자 | 변경 내용 |
|---|---|---|---|
| 2026.10.14 | 0.9.0 | [우진환](https://github.com/313mlclub) | 문서 초안 작성 |
| 2026.10.17 | 1.0.0 | [우진환](https://github.com/313mlclub) | 문서 서식 적용 |
| 2026.10.24 | 1.1.0 | [유승호](https://github.com/hahaysh) | PDF 기반 Markdown 정리 및 검토 |
