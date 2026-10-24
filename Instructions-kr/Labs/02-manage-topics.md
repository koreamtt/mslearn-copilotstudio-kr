---
lab:
  title: Copilot Studio 에이전트의 토픽 관리
  module: 토픽을 사용하여 에이전트 대화 설계
  description: 이 랩에서는 Copilot을 사용하여 에이전트와 설명 기반 토픽을 만들고, 노드를 추가하고, 엔터티를 사용하고, 변수를 관리합니다.
  duration: 45 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
---

# Copilot Studio 에이전트의 토픽 관리

## 시나리오

이 연습에서는 다음 작업을 수행합니다.

- 에이전트 만들기
- 기존 토픽 관리
- Copilot을 사용하여 토픽 만들기 및 편집
- 변수 범위 구성
- 수동으로 토픽 만들기
- 노드 만들기 및 편집
- 에이전트 테스트

이 연습을 완료하는 데 약 **45**분이 소요됩니다.

## 학습 내용

- 토픽이 생성형 AI 응답을 보완하는 방식
- 구조화된 대화를 적용하기 위해 토픽을 사용하는 경우
- 자연어를 사용하여 토픽을 만들고 구체화하는 방법
- 변수를 사용하는 방법

## 랩의 주요 단계

- Copilot을 사용하여 에이전트 만들기
- 불필요한 토픽 검토 및 사용 중지
- Copilot을 사용하여 토픽 만들기
- 자연어를 사용하여 토픽 콘텐츠 편집
- 토픽 동작 테스트

## 필수 구성 요소

- Microsoft Entra ID 계정
- Copilot Studio 라이선스 또는 [무료 평가판](https://go.microsoft.com/fwlink/p/?linkid=2252605) 등록
- 에이전트 및 관련 자산을 만들 수 있는 Power Platform 환경과 솔루션에 대한 액세스 권한
- 다음 중 하나를 사용할 수 있습니다.
  - **ILT Setup** 랩에서 만든 환경과 **`Lab Exercises`(랩 연습)** 솔루션
  - 자체 기존 환경과 솔루션
- 환경과 솔루션을 아직 준비하지 않았다면 계속하기 전에 **ILT Setup** 랩의 단계를 완료합니다.

> [!IMPORTANT]
> 현재 미리 보기로 제공되는 새로운 Copilot Studio 환경이 표시될 수 있습니다. 이 랩에서는 현재 Copilot Studio 인터페이스를 사용하므로 일부 단계와 스크린샷이 미리 보기 환경과 일치하지 않을 수 있습니다. 랩 지침을 올바르게 수행하려면 연습 전체에서 클래식 Copilot Studio UI 환경을 사용합니다.

## 핵심 개념: 에이전트 구성 요소 및 동작

생성형 오케스트레이션을 사용하도록 설정하면 에이전트가 지침, 지식, 토픽 및 도구를 사용하여 응답을 동적으로 생성할 수 있습니다.

토픽은 특히 다음 작업이 필요한 경우에 유용합니다.

- 필수 정보를 단계별로 수집
- 질문 순서 제어
- 변수에 응답 저장
- 예측 가능한 결과 보장

## 연습 1 - 에이전트 만들기

이 연습에서는 자연어를 사용하여 정부 복리후생 관련 질문에 답변하는 새 에이전트를 만듭니다.

### 작업 1.1 – 보험 청구를 검토하는 에이전트 만들기

1. `https://copilotstudio.microsoft.com/`의 **Copilot Studio** 홈페이지로 이동합니다.

1. **Copilot Studio** 클래식 환경을 사용하고 있는지 확인합니다. 클래식 환경이 아니면 계속하기 전에 클래식 환경으로 전환합니다.

1. 페이지 위쪽에서 이 연습에 사용할 환경에서 작업 중인지 확인합니다.

1. 왼쪽 탐색 영역에서 **에이전트(Agents)** 를 선택합니다.

1. *에이전트가 수행해야 할 작업을 설명하여 빌드 시작(Start building by describing what your agent needs to do)* 텍스트 상자의 왼쪽 아래에서 **톱니바퀴(Cog)** 이미지로 표시되는 **에이전트 설정(Agent Settings)** 아이콘을 선택합니다.

   ![에이전트 설정 대화 상자의 스크린샷.](../media/agent-settings-dialog.png)

1. 에이전트의 기본 언어를 **영어(미국)(English (United States))** 로 그대로 둡니다.

1. **솔루션(Solution)** 드롭다운에서 **`Lab Exercises`(랩 연습)** 또는 이 연습에 사용할 다른 솔루션을 선택합니다.

1. *스키마 이름(Schema name)* 에 `insuranceagent`를 입력합니다.

1. **업데이트(Update)** 를 선택합니다.

1. *에이전트가 수행해야 할 작업을 설명하여 빌드 시작(Start building by describing what your agent needs to do)* 텍스트 상자에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   You are an agent that assists with reviewing insurance claims including damage assessment details and repair estimates.
   ```

   ```prompt
   손해 평가 세부 정보와 수리 견적을 포함하여 보험 청구 검토를 지원하는 에이전트입니다.
   ```

1. **보내기(Send)** 아이콘을 선택합니다.

   에이전트 프로비저닝이 완료되면 에이전트 구성을 계속할 수 있습니다.

## 연습 2 - 토픽 관리

이 연습에서는 에이전트를 인계할 상담원이 없으므로 Escalate 시스템 토픽을 사용하지 않도록 설정합니다. 사용하지 않는 시스템 토픽을 사용 중지하면 생성형 오케스트레이션이 응답 방법을 결정할 때 모호성을 줄이는 데 도움이 됩니다.

### 작업 2.1 – 토픽 사용 중지

1. **토픽(Topics)** 탭을 선택합니다.

1. **시스템(System)** 필터를 선택합니다.

1. **Escalate** 토픽을 찾습니다.

1. **Escalate** 토픽의 **사용(Enabled)** 토글을 **끔(Off)** 으로 설정합니다.

   ![Copilot Studio 포털에서 제거되고 사용 중지된 토픽.](../media/topic-escalate-disabled.png)

사용하지 않는 토픽을 사용 중지하면 여러 토픽이나 생성형 응답이 동일한 요청을 처리할 수 있을 때 모호성을 줄이는 데 도움이 됩니다.

## 연습 3 - 자연어로 토픽 만들기

이 연습에서는 Copilot을 사용하여 설명에서 토픽을 만듭니다. 이를 통해 생성형 AI가 초기 구조의 초안을 작성하게 한 다음 구체화할 수 있습니다.

### 작업 3.1 – 설명에서 토픽 추가

1. **+ 토픽 추가(+ Add a topic)** 를 선택한 다음 **Copilot을 사용하여 설명에서 추가(Add from description with Copilot)** 를 선택합니다. 새 대화 상자가 나타납니다.

   ![Copilot을 사용하여 토픽을 만드는 옵션.](../media/topic-create-from-description-1.png)

   ![Copilot을 사용하여 토픽을 만드는 대화 상자.](../media/topic-create-from-description-2.png)

1. **토픽 이름 지정(Name your topic)** 텍스트 상자에 **`Customer Details`(고객 세부 정보)** 를 입력합니다.

1. **다음을 수행하는 토픽 만들기(Create a topic to...)** 텍스트 상자에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Ask the customer for their name and email address
   ```

   ```prompt
   고객에게 이름과 이메일 주소를 질문합니다
   ```

1. **만들기(Create)** 를 선택합니다.

1. **저장(Save)** 을 선택합니다.

### 작업 3.2 – 자연어를 사용하여 노드 편집

1. **에이전트 테스트(Test your agent)** 패널이 열려 있으면 닫습니다.

1. **Customer Details** 창의 오른쪽에 **Copilot으로 편집(Edit with Copilot)** 패널이 표시되지 않으면 제작 캔버스 위쪽에 있는 **Copilot** 아이콘을 선택합니다.

   ![Copilot으로 편집 아이콘의 스크린샷.](../media/edit-with-copilot.png)

1. 두 번째 **질문(Question)** 노드인 **What is your email address?** 를 선택합니다.

   ![Copilot으로 편집 아이콘의 스크린샷.](../media/copilot-email-address-node.png)

1. **Copilot으로 편집(Edit with Copilot)** 패널의 **수행할 작업(What do you want to do?)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Change "What is your email address?" to say thank you to the Name variable from the previous node and then proceed to ask the email address question.
   ```

   ```prompt
   "What is your email address?"를 이전 노드의 Name 변수에 감사 인사를 한 다음 이메일 주소를 질문하도록 변경합니다.
   ```

1. **업데이트(Update)** 를 선택합니다.

   ![프롬프트가 포함된 Copilot으로 편집 패널의 스크린샷.](../media/edit-with-copilot-panel.png)

   ![Name 변수를 포함하도록 업데이트된 메시지의 스크린샷.](../media/message-updated-name-variable.png)

   > [!NOTE]
   > 업데이트된 메시지는 이전 질문 노드에서 수집한 **Name** 변수를 참조해야 하며 스크린샷과 비슷하게 표시되어야 합니다. **Copilot으로 편집(Edit with Copilot)** 에서 질문 노드를 올바르게 업데이트하지 못한 경우 **실행 취소(Undo)** 를 선택하고 다른 프롬프트로 다시 시도합니다.

1. **저장(Save)** 을 선택합니다.

### 작업 3.3 – 자연어를 사용하여 Adaptive Card 노드 추가

기존 노드를 수정하는 것 외에도 Copilot을 사용하여 새 노드를 추가할 수 있습니다.

1. 노드가 선택되지 않도록 제작 캔버스의 빈 영역을 선택합니다.

1. **Copilot으로 편집(Edit with Copilot)** 패널의 **수행할 작업(What do you want to do?)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Summarize the information collected in an adaptive card
   ```

   ```prompt
   수집한 정보를 Adaptive Card로 요약합니다
   ```

1. **업데이트(Update)** 를 선택합니다.

   Adaptive Card가 포함된 메시지 노드가 토픽 끝에 추가됩니다.

   ![Adaptive Card가 포함된 메시지 노드의 스크린샷.](../media/message-node-adaptive-card.png)

1. Adaptive Card에서 **미디어(Media)** 상자를 선택합니다. 페이지 오른쪽에 Adaptive Card 속성이 표시됩니다.

   ![Adaptive Card 속성의 스크린샷.](../media/adaptive-card-properties.png)

   Adaptive Card 수식은 위와 비슷하게 표시되어야 합니다. Adaptive Card가 크게 다르면 다음 수식으로 바꿀 수 있습니다.

   ```powerfx
   {
   type: "AdaptiveCard", 
       body: 
       [
           {
               type: "TextBlock",
               size: "Medium",
               weight: "Bolder",
               text: "Summary"
           },
           {
               type: "FactSet",
               facts: 
               [
                   {
                       title: "Full Name",
                       value: Text(Topic.Name)
                   },
                   {
                       title: "Email Address",
                       value: Text(Topic.EmailAddress)
                   }
               ]
           },
           {
               type: "TextBlock",
               text: "Thank you for providing the information."
           }
       ]
   }
   ```

### 작업 3.4 – 자연어를 사용하여 질문 노드 추가

1. 제작 캔버스의 빈 공간을 선택하여 노드가 선택되지 않았는지 확인합니다.

1. **Copilot** 아이콘을 선택하여 **Copilot으로 편집(Edit with Copilot)** 창을 다시 엽니다.

1. **수행할 작업(What do you want to do?)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Add a new multiple choice question to prompt the user if the details are correct with two options Yes or No
   ```

   ```prompt
   세부 정보가 올바른지 사용자에게 묻는 새 객관식 질문을 추가하고 Yes와 No 두 가지 옵션을 제공합니다
   ```

1. **업데이트(Update)** 를 선택합니다.

1. 사용자가 선택할 수 있는 옵션이 포함된 새 질문 노드가 토픽 끝에 추가됩니다.

   ![Yes 및 No 옵션이 있는 새 질문 노드의 스크린샷.](../media/new-question-node.png)

1. **저장(Save)** 을 선택합니다.

## 연습 4 - 변수 범위

다른 토픽에서 변수에 액세스할 수 있도록 설정합니다.

### 작업 4.1 - 변수 범위 구성

1. **토픽(Topics)** 탭을 선택합니다.

1. **Customer Details** 토픽을 선택합니다.

1. 위쪽 표시줄에서 **변수(Variables)** 를 선택하여 **변수(Variables)** 창을 엽니다. **더 보기(More)** \> **변수(Variables)** 를 선택해야 할 수도 있습니다.

1. **토픽(Topic)** 변수를 선택하여 펼칩니다.

1. 세 토픽 변수의 오른쪽 확인란을 선택합니다. 이렇게 하면 에이전트의 다른 토픽에서도 변수를 사용할 수 있습니다.

   ![변수 창의 스크린샷.](../media/variables-pane.png)

1. **저장(Save)** 을 선택합니다.

## 연습 5 - 빈 토픽 만들기

이 연습에서는 **`Estimate Repair`(수리 견적)** 토픽을 만들고 노드를 추가한 다음 Customer Details 토픽을 호출합니다.

### 작업 5.1 - 빈 토픽 만들기

1. **토픽(Topics)** 탭을 선택합니다.

1. **+ 토픽 추가(+ Add a topic)** 를 선택한 다음 **빈 토픽에서 시작(From blank)** 을 선택합니다.

1. **세부 정보(Details)** 아이콘을 선택하여 **토픽 세부 정보(Topic details)** 창을 엽니다. **더 보기(More)** \> **세부 정보(Details)** 를 선택해야 할 수도 있습니다.

1. **이름(Name)** 필드에 **`Estimate Repair`(수리 견적)** 를 입력합니다.

1. **모델 설명(Model description)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Use this topic when a repair estimate for an insurance claim must be booked with the customer
   ```

   ```prompt
   고객과 보험 청구 수리 견적 일정을 예약해야 할 때 이 토픽을 사용합니다
   ```

   ![토픽 세부 정보 대화 상자의 스크린샷.](../media/topic-details.png)

1. **저장(Save)** 을 선택합니다.

### 작업 5.2 - 트리거 유형 확인

1. 토픽 위쪽의 **트리거(Trigger)** 노드를 선택합니다. 트리거 유형이 **에이전트가 선택(The agent chooses)** 으로 설정되어 있는지 확인합니다.

   > [!NOTE]
   > 생성형 오케스트레이션을 사용하도록 설정하면 에이전트는 이 설명을 사용하여 토픽을 사용할 시점을 결정합니다.

### 작업 5.3 - 메시지 노드 추가

1. 트리거 노드 아래의 **+** 아이콘을 선택한 다음 **메시지 보내기(Send a message)** 를 선택합니다.

   ![노드를 추가하는 스크린샷.](../media/add-message-node.png)

1. **메시지 입력(Enter a message)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Hi, I can help you with booking a repair estimate.
   ```

   ```prompt
   안녕하세요. 수리 견적 예약을 도와드리겠습니다.
   ```

1. **저장(Save)** 을 선택합니다.

### 작업 5.4 - Customer Details 토픽으로 라우팅

1. **메시지(Message)** 노드 아래의 **+** 아이콘을 선택합니다.

1. **토픽 관리(Topic management)** \> **다른 토픽으로 이동(Go to another topic)** \> **Customer Details** 를 선택합니다.

   ![토픽 관리 노드를 추가하는 스크린샷.](../media/topic-management-node.png)

1. **저장(Save)** 을 선택합니다.

### 작업 5.5 - 조건 노드 추가

1. **토픽(Topic)** 노드 아래의 **+** 아이콘을 선택한 다음 **조건 추가(Add a condition)** 를 선택합니다.

1. **조건(Condition)** 노드에서 **DetailsCorrect** 변수를 선택합니다.

1. **같음(is equal to)** 을 선택합니다.

1. **Yes**를 선택합니다.

   ![조건 노드를 추가하는 스크린샷.](../media/condition-node.png)

1. **저장(Save)** 을 선택합니다.

### 작업 5.6 - 질문 노드 추가

1. 왼쪽 **조건(Condition)** 노드 아래의 **+** 아이콘을 선택한 다음 **질문하기(Ask a question)** 를 선택합니다.

1. **메시지 입력(Enter a message)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   What date and time would you like to book the repair estimate?
   ```

   ```prompt
   수리 견적을 어느 날짜와 시간으로 예약하시겠습니까?
   ```

1. **식별(Identify)** 에서 **날짜 및 시간(Date and time)** 을 선택합니다.

1. **사용자 응답 저장 형식(Save user response as)** 에서 변수를 선택하고 **변수 이름(Variable name)** 에 `VisitDateTime`을 입력합니다.

1. 왼쪽 **질문(Question)** 노드 아래의 **+** 아이콘을 선택한 다음 **메시지 보내기(Send a message)** 를 선택합니다.

1. **메시지 입력(Enter a message)** 필드에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   Great! Let me get that scheduled for you.
   ```

   ```prompt
   좋습니다! 해당 일정으로 예약해 드리겠습니다.
   ```

1. 해당 메시지 노드 다음에 **토픽 관리(Topic management)** \> **모든 토픽 종료(End all topics)** 를 선택하여 토픽을 종료하는 노드를 추가합니다.

1. **저장(Save)** 을 선택합니다.

### 작업 5.7 - 에이전트 지침 업데이트

1. **개요(Overview)** 탭을 선택합니다.

1. **지침(Instructions)** 섹션에서 **편집(Edit)** 을 선택합니다.

1. 에이전트 지침의 *# Skills* 아래에 `Use the`를 입력한 다음 `/`를 입력하고 **Estimate Repair** 토픽을 선택한 후 `when a repair estimate is required.`를 입력합니다. 완성되는 지침은 다음과 같습니다. 한국어 지침을 사용하는 경우에도 `<Estimate Repair>` 자리 표시자는 입력하지 않고 `/`를 사용하여 토픽 참조를 삽입합니다.

   ```prompt
   Use the <Estimate Repair> topic when a repair estimate is required.
   ```

   ```prompt
   수리 견적이 필요한 경우 <Estimate Repair> 토픽을 사용합니다.
   ```

   ![에이전트 지침에서 토픽을 참조하는 스크린샷.](../media/add-topic-to-instructions.png)

1. **저장(Save)** 을 선택합니다.

## 연습 6 - 에이전트 테스트

이 연습에서는 토픽 라우팅을 테스트하고 대화가 예상된 단계별 흐름을 따르는지 확인합니다.

### 작업 6.1 - Estimate Repair 토픽 테스트

1. 페이지 오른쪽 위에서 **테스트(Test)** 아이콘을 선택하여 **테스트(Test)** 창을 엽니다.

1. **테스트(Test)** 창에서 변수 **{x}** 아이콘 옆의 줄임표(**...**)를 선택하고 **테스트할 때 활동 맵 표시(Show activity map when testing)** 를 **켬(On)** 으로, **토픽 간 추적(Track between topics)** 을 **끔(Off)** 으로 전환합니다.

   ![활동 맵 표시.](../media/show-activity-map.png)

1. **테스트 창(Test pane)** 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. **Conversation Start** 메시지가 표시되면 에이전트가 대화를 시작합니다. 토픽을 트리거하려면 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   I need to book a repair estimate
   ```

   ```prompt
   수리 견적을 예약해야 합니다
   ```

1. 고객 이름을 묻는 질문으로 대화가 시작되어야 합니다.

   ![대화의 스크린샷.](../media/topic-conversation-1.png)

1. 이름을 입력합니다.

1. 이메일 주소를 입력합니다.

1. 정보를 입력하면 입력한 정보가 Adaptive Card에 표시되고 세부 정보가 올바른지 묻습니다. **Yes**를 선택합니다.

   대화 흐름이 **Estimate Repair** 토픽으로 돌아가는지 확인합니다.

1. **What date and time do you want to book the repair estimate?** 프롬프트에 다음 영문 또는 한국어 응답 중 하나를 입력합니다.

   ```prompt
   Tomorrow 10:00 AM
   ```

   ```prompt
   내일 오전 10시
   ```

   에이전트가 수리 견적 일정이 예약되었다는 확인 메시지로 응답합니다.

## 요약

이 랩에서는 Customer Details 및 Estimate Repair 토픽을 만들고 노드를 사용하여 구조화된 단계별 상호 작용을 적용하면서 생성형 AI를 계속 사용했습니다. 또한 Customer Details에서 수집한 정보를 여러 토픽에서 사용할 수 있도록 변수 범위를 구성했습니다.
