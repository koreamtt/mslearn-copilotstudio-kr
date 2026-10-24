---
lab:
  title: 새로운 Copilot Studio 환경을 사용하여 에이전트 만들기
  module: Microsoft Copilot Studio에서 에이전트 만들기
  description: 이 랩에서는 새로운 Copilot Studio 환경을 사용하여 지침 기반 에이전트를 만들고, 미리 빌드된 작업을 추가하며, 자율 추론 동작을 테스트합니다.
  duration: 30 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
---

# 새로운 Copilot Studio 환경을 사용하여 에이전트 만들기

## 시나리오

이 연습에서는 다음 작업을 수행합니다.

- 새로운 Copilot Studio 환경으로 전환
- 자연어 지침을 사용하여 에이전트 만들기
- 에이전트가 자율적으로 사용할 수 있는 미리 빌드된 작업 추가
- 에이전트를 테스트하고 추론 동작 관찰
- 테스트 결과에 따라 지침 개선

이 연습을 완료하는 데 약 **30**분이 소요됩니다.

## 학습할 내용

- 새로운 Copilot Studio 환경과 클래식 인터페이스의 차이점
- 토픽 트리 대신 지침을 사용하여 에이전트를 구성하는 방법
- 에이전트가 지식과 작업을 선택하기 위해 자율적으로 추론하는 방법
- 에이전트 동작을 개선하도록 지침을 반복해서 수정하는 방법

## 랩의 주요 단계

- 새로운 Copilot Studio 환경으로 전환
- 설명을 사용하여 에이전트 만들기
- 에이전트 지침 작성 및 개선
- 미리 빌드된 작업 추가
- 테스트 및 반복 개선

## 필수 구성 요소

- Microsoft Entra ID 계정이 있어야 합니다.
- Copilot Studio 라이선스가 있거나 [무료 평가판](https://go.microsoft.com/fwlink/p/?linkid=2252605)에 가입해야 합니다.
- 에이전트와 관련 자산을 만들 수 있는 Power Platform 환경 및 솔루션에 액세스할 수 있어야 합니다.
- 다음 중 하나를 사용할 수 있습니다.
  - **ILT Setup** 랩에서 만든 환경 및 **`Lab Exercises`(랩 연습)** 솔루션
  - 사용 중인 기존 환경 및 솔루션
- 환경과 솔루션이 아직 준비되지 않았다면 계속하기 전에 **ILT Setup** 랩의 단계를 완료합니다.

> [!IMPORTANT]
> 새로운 Copilot Studio 환경은 클래식 토픽 제작 캔버스를 대체하는 새롭게 디자인된 인터페이스입니다. 이 랩의 단계와 스크린샷은 새로운 환경을 기준으로 합니다. 환경에 클래식 인터페이스가 표시되면 계속하기 전에 안내에 따라 새로운 환경으로 전환합니다.

## 핵심 개념: 지침 기반 에이전트

새로운 Copilot Studio 환경은 토픽 제작 캔버스를 더 간단한 지침 기반 모델로 대체합니다.

| 클래식 환경 | 새로운 환경 |
|---|---|
| 토픽 트리와 트리거 문구로 에이전트 동작 정의 | 자연어 지침으로 에이전트 동작 정의 |
| 제작자가 노드별로 명시적인 대화 흐름 구성 | 에이전트가 응답 방법을 동적으로 추론 |
| 토픽, 조건 및 분기로 대화 라우팅 제어 | 지침, 지식 및 작업으로 에이전트가 수행할 작업 결정 |
| 작업을 사용하려면 Power Automate 워크플로를 만들고 입력/출력을 구성한 후 도구로 추가해야 함 | Copilot Studio에서 미리 빌드된 커넥터 작업을 직접 추가하므로 워크플로를 제작할 필요가 없음 |

새로운 환경은 개방형이며 컨텍스트에 따라 달라지는 대화를 처리해야 하는 에이전트에 가장 적합합니다. 이후 랩에서 다루는 클래식 환경은 구조화된 데이터를 특정 순서로 수집하는 경우처럼 보장되고 감사 가능한 단계 순서가 필요할 때 여전히 적합합니다.

## 연습 1 - 새로운 Copilot Studio 환경으로 전환

### 작업 1.1 – 새로운 환경 열기

1. `https://copilotstudio.preview.microsoft.com/`의 새로운 **Copilot Studio** 환경 홈 페이지로 이동하고 메시지가 표시되면 로그인합니다.

1. 왼쪽 탐색 영역 아래쪽에서 현재 환경 이름을 선택한 다음, 이 연습에 사용할 환경인지 확인하거나 해당 환경으로 전환합니다.

### 작업 1.2 – 새로운 인터페이스 검토

에이전트를 만들기 전에 잠시 새로운 환경의 구성을 살펴봅니다.

1. 왼쪽 탐색 영역의 주요 섹션인 **홈(Home)**, **에이전트 운영(Agent Ops)**, **채팅(Chat)**, **에이전트(Agents)**, **워크플로(Workflows)**를 확인합니다.

1. **에이전트(Agents)** 페이지에는 기존 에이전트가 표시됩니다. 새로운 환경에서 만든 에이전트에는 토픽 캔버스가 없습니다. 에이전트 동작은 에이전트의 **개요(Overview)** 페이지에 있는 지침, 지식 및 작업으로만 정의됩니다.

1. 탐색 영역에 **토픽(Topics)** 섹션이 없다는 점을 확인합니다. 새로운 환경에서는 작업과 지침이 토픽을 대신합니다.

## 연습 2 - 에이전트 만들기

이 연습에서는 가상 회사 Contoso의 IT 지원 에이전트를 만듭니다. 이 에이전트는 직원이 일반적인 IT 문제를 해결하고 지원 티켓을 제출하도록 돕습니다.

### 작업 2.1 – 에이전트 만들기

1. 왼쪽 탐색 영역에서 **홈(Home)**을 선택합니다.

1. **홈(Home)** 페이지의 빌드 프롬프트 상자에 다음 설명을 입력합니다.

   ```prompt
   You are an IT support agent for Contoso. You help employees troubleshoot common IT issues such as password resets, software installation problems, and network connectivity. When you cannot resolve an issue, you help the employee submit a support ticket.
   ```

   ```prompt
   Contoso의 IT 지원 에이전트입니다. 직원이 암호 재설정, 소프트웨어 설치 문제, 네트워크 연결과 같은 일반적인 IT 문제를 해결하도록 돕습니다. 문제를 해결할 수 없으면 직원이 지원 티켓을 제출하도록 돕습니다.
   ```

   > [!NOTE]
   > 일부 환경에서는 표준 URL을 통해 Copilot Studio에 액세스할 때 **홈(Home)** 페이지에 빌드 프롬프트 상자가 표시되지 않을 수 있습니다. 프롬프트 상자를 사용할 수 없다면 미리 보기 URL `https://copilotstudio.preview.microsoft.com/`에서 Copilot Studio가 열렸는지 확인한 후 연습을 계속합니다.

   > [!NOTE]
   > 새로운 환경에서는 설명을 사용하여 초기 지침 세트를 자동으로 생성합니다. 계속하기 전에 이를 검토합니다.

1. 명확히 하기 위한 질문이 표시되면 에이전트가 더 정확한 지침을 생성할 수 있도록 답변합니다. 예를 들면 다음과 같습니다.

   - 직원이 IT 지원 티켓을 제출하는 방법을 묻는 경우 ServiceNow, Jira, Dynamics 365 또는 Zendesk 대신 IT 지원 센터에 지원 요청 전자 메일을 보내는 옵션을 선택합니다.
   - 에이전트가 기술 자료, SharePoint 사이트 또는 웹 사이트를 참조해야 하는지 묻는 경우 외부 지식 원본이 필요하지 않음을 나타내는 옵션을 선택합니다.

   질문을 진행하려면 **계속(Continue)**을 선택하고, 해당하지 않는 질문은 **건너뛰기(Skip)**를 선택합니다. 완료되면 **제출(Submit)**을 선택합니다.

   > [!NOTE]
   > 설명과 환경에 따라 명확히 하기 위한 질문이 달라지거나 전혀 표시되지 않을 수 있습니다. 정확히 동일한 질문이나 답변 옵션을 기대하기보다 랩 시나리오에 맞게 답변합니다.

1. 에이전트가 지원 요청을 보낼 때 사용할 전자 메일 주소를 입력하라는 메시지가 표시되면 관리자 전자 메일 주소를 입력한 후 **제출(Submit)**을 선택합니다.

1. 자동 생성된 지침을 검토하고 수락한 후 에이전트를 만듭니다.

1. 오른쪽 **아티팩트(Artifacts)** 패널에서 에이전트를 선택하여 **빌드(Build)** 탭을 엽니다.

### 작업 2.2 – 자동 생성된 지침 검토 및 개선

1. 에이전트의 **빌드(Build)** 탭에서 **지침(Instructions)** 섹션을 찾습니다.

1. 설명을 바탕으로 생성된 지침을 검토합니다. 지침에는 에이전트의 목적, 어조 및 일반적인 동작이 설명되어 있어야 합니다.

1. **지침(Instructions)** 섹션에 다음 지침을 추가하여 업데이트한 후 **저장(Save)**을 선택합니다.

   ```prompt
   ## Guidelines
   - Always respond in a professional and friendly tone.
   - For password reset requests, direct the employee to the self-service portal at https://aka.ms/sspr before offering to raise a ticket.
   - For issues you cannot resolve, collect the employee's name, email address, and a brief description of the issue before submitting a ticket.
   - Do not speculate about hardware failures. Always recommend contacting the IT desk directly for physical hardware issues.
   - When an employee's issue cannot be resolved, use the Send an email action to notify the IT helpdesk at helpdesk@contoso.com with the employee's name, email, and issue description.
   ```

   ```prompt
   ## 지침
   - 항상 전문적이고 친절한 어조로 응답합니다.
   - 암호 재설정 요청의 경우 티켓 생성을 제안하기 전에 직원에게 https://aka.ms/sspr의 셀프 서비스 포털을 안내합니다.
   - 해결할 수 없는 문제의 경우 티켓을 제출하기 전에 직원의 이름, 전자 메일 주소 및 문제에 대한 간략한 설명을 수집합니다.
   - 하드웨어 오류를 추측하지 않습니다. 물리적 하드웨어 문제는 항상 IT 지원 센터에 직접 문의하도록 권장합니다.
   - 직원의 문제를 해결할 수 없는 경우 Send an email 작업을 사용하여 직원의 이름, 전자 메일 및 문제 설명과 함께 helpdesk@contoso.com의 IT 지원 센터에 알립니다.
   ```

   > [!NOTE]
   > 새로운 환경에서는 지침이 에이전트 동작을 제어하는 기본 수단입니다. 잘 작성된 지침은 추가 구성의 필요성을 줄이고 에이전트의 예측 가능성을 높입니다.

## 연습 3 - 테스트 및 개선

이 연습에서는 에이전트를 테스트하고 응답하기 전에 에이전트가 추론하는 방식을 관찰합니다.

### 작업 3.1 – 미리 보기 탭 열기

1. 페이지 위쪽의 **미리 보기(Preview)** 탭을 선택하여 에이전트를 테스트합니다.

1. 에이전트를 테스트하면 각 응답 위에 추론 요약이 자동으로 표시되어 에이전트가 수행할 작업을 결정한 방법을 설명합니다. 해당 요약에서 **자세히 보기(Show more)**를 선택하여 전체 추론 추적을 펼칩니다.

   > [!NOTE]
   > 추론 추적은 새로운 환경의 핵심 기능입니다. 에이전트가 고려한 지식 원본이나 작업과 그 이유를 보여 줍니다. 예를 들어 **로드된 기술(Loaded Skill)** 항목은 에이전트가 호출한 작업 또는 기술을 나타냅니다.

### 작업 3.2 – 지침 테스트

1. **미리 보기(Preview)** 탭 위쪽에서 **새 채팅(New chat)**을 선택합니다.

1. 다음 프롬프트를 입력합니다.

   ```prompt
   I forgot my password and cannot log in.
   ```

   ```prompt
   암호를 잊어버려 로그인할 수 없습니다.
   ```

   작성한 지침에 따라 에이전트는 티켓 생성을 제안하기 전에 셀프 서비스 포털을 안내해야 합니다.

### 작업 3.3 – 에이전트의 추론 동작 테스트

1. **미리 보기(Preview)** 탭 위쪽에서 **새 채팅(New chat)**을 선택합니다.

1. 다음 프롬프트를 입력합니다.

   ```prompt
   My laptop will not turn on at all.
   ```

   ```prompt
   노트북 전원이 전혀 켜지지 않습니다.
   ```

   작성한 지침에 따라 에이전트는 하드웨어 오류의 원격 문제 해결을 거부하고 IT 지원 센터에 직접 문의하도록 권장해야 합니다. 에이전트가 사용자를 대신해 지원 티켓을 제출하겠다고 제안할 수도 있습니다.

1. 메시지가 표시되면 이름, 전자 메일 및 문제에 대한 간략한 설명을 제공합니다.

### 작업 3.4 – 테스트 결과에 따라 지침 개선

1. 세 번의 테스트 세션에서 에이전트가 응답한 방식을 검토합니다.

1. 응답이 의도한 동작과 일치하지 않으면 **빌드(Build)** 탭을 선택하고 **지침(Instructions)** 섹션에서 관련 지침을 조정합니다.

   예를 들어 에이전트가 암호 재설정 시 셀프 서비스 포털을 언급하지 않았다면 지침을 더 명확하게 작성합니다.

   ```prompt
   - For ALL password-related requests, always mention https://aka.ms/sspr as the first step before any other assistance.
   ```

   ```prompt
   - 모든 암호 관련 요청에서는 다른 지원을 제공하기 전에 항상 첫 번째 단계로 https://aka.ms/sspr을 안내합니다.
   ```

1. **게시(Publish)**를 선택한 다음 **에이전트 게시(Publish agent)**를 선택합니다. 에이전트가 게시되면 **완료(Done)**를 선택하고 해당 시나리오를 다시 테스트합니다.

> [!NOTE]
> 지침을 반복해서 수정하는 작업은 새로운 환경에서 사용하는 기본 튜닝 메커니즘입니다. 표현을 조금만 바꿔도 에이전트 동작이 크게 달라질 수 있습니다.

## 요약

이 랩에서는 새로운 Copilot Studio 환경을 사용하여 지침 기반 IT 지원 에이전트를 만들었습니다. 자연어 지침만으로 동작을 구성하고, Power Automate 워크플로를 만들거나 페이지를 벗어나지 않고도 Copilot Studio에서 미리 빌드된 커넥터 작업을 직접 추가했습니다. 도구를 추가하기 위해 워크플로를 제작하고 입력과 출력을 구성한 후 별도로 게시해야 했던 랩 03과 비교하면, 새로운 환경에서는 간단한 작업의 제작 노력이 크게 줄어듭니다. 또한 미리 보기 창의 추론 추적을 사용하여 에이전트가 응답을 생성하기 전에 수행할 작업을 결정한 방식을 관찰했습니다. 이제 클래식 환경과 새로운 환경을 모두 사용해 보았으므로, 개방형 대화에는 지침 기반 접근 방식을 사용하고 보장되고 감사 가능한 단계 순서가 필요한 경우에는 클래식 토픽과 워크플로를 사용하는 등 각 시나리오에 적합한 방식을 선택할 수 있습니다.
