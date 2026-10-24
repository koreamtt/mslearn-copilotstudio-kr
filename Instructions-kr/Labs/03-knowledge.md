---
lab:
  title: Copilot Studio 에이전트의 지식 관리
  module: 지식 원본으로 에이전트 기반 설정
  description: 이 랩에서는 Copilot을 사용하여 에이전트를 만들고, Dataverse 테이블을 만들고, 에이전트에 지식을 추가하고, 생성형 AI를 구성합니다.
  duration: 60 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
---

# Copilot Studio 에이전트의 지식 관리

## 시나리오

이 연습에서는 다음 작업을 수행합니다.

- Dataverse 테이블 만들기
- 에이전트 만들기
- 지식 원본으로 사용할 파일 업로드
- 지식 원본으로 공개 웹 사이트 추가
- 지식 원본으로 Dataverse 테이블 추가
- 생성형 오케스트레이션 설정 구성
- 생성형 답변 만들기 노드 구성
- Microsoft Teams에 에이전트 게시

이 연습을 완료하는 데 약 **60**분이 소요됩니다.

## 학습 내용

- 에이전트에 지식 원본을 추가하는 방법
- 생성형 오케스트레이션과 생성형 답변 동작을 구성하는 방법

## 랩의 주요 단계

- Copilot을 사용하여 Dataverse 테이블 만들기
- Copilot을 사용하여 에이전트 만들기
- 지식 원본 추가
- 생성형 AI 구성
- 에이전트 게시

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

생성형 오케스트레이션을 사용하도록 설정하면 에이전트가 지침, 지식, 토픽 및 도구를 사용하여 응답을 동적으로 생성할 수 있습니다. 여러 유형의 지식 원본을 사용하여 에이전트의 답변 기반을 설정할 수 있으며, 여러 설정이 생성형 응답의 생성 방식에 영향을 줍니다.

## 연습 1 - Dataverse에서 테이블 만들기

이 연습에서는 에이전트의 지식 원본으로 사용할 Dataverse 테이블을 만듭니다.

### 작업 1.1 – 경비 청구용 테이블 만들기

1. 웹 브라우저에서 `https://make.powerapps.com/`의 **Power Apps Maker 포털**로 이동하고 메시지가 표시되면 로그인합니다. 시작 메시지는 건너뜁니다.

1. 페이지 위쪽에서 이 연습에 사용할 환경에서 작업 중인지 확인합니다.

   ![Maker 포털에서 환경을 선택합니다.](../media/select-powerapps-environment.png)

1. **Maker 포털**의 왼쪽 탐색 영역에서 **테이블(Tables)** 을 선택합니다.

   ![Maker 포털의 Dataverse 테이블.](../media/dataverse-tables.png)

1. **Copilot 시작(Get started with Copilot)** 타일을 선택합니다.

1. **Copilot 시작(Get started with Copilot)** 대화 상자에서 **테이블 옵션(Table options)** 아이콘을 선택한 다음 **테이블 하나(One table)** 를 선택합니다.

   ![Maker 포털의 테이블 옵션.](../media/dataverse-table-options.png)

1. *Copilot에서 빌드할 테이블 설명(Describe the tables you want Copilot to build)* 텍스트 상자에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   A table to store and process expense claims with an Expense Title, Expense Type (Accommodation, Meals, Entertainment or Travel), Expense Date, Submission Date, Approved Date, Amount Requested, Amount Approved, and Expense Status (Submitted, Evaluating, Approved, Rejected).
   ```

   ```prompt
   Expense Title, Expense Type(Accommodation, Meals, Entertainment 또는 Travel), Expense Date, Submission Date, Approved Date, Amount Requested, Amount Approved 및 Expense Status(Submitted, Evaluating, Approved, Rejected)가 포함된 경비 청구를 저장하고 처리하는 테이블입니다.
   ```

1. **생성(Generate)** 을 선택합니다.

    > [!NOTE]
    > 생성된 테이블 스키마는 이 랩의 스크린샷과 약간 다를 수 있습니다. 열 이름이나 서식에 사소한 차이가 있는 것은 정상입니다.

1. 테이블이 만들어집니다. 테이블 이름을 기록해 둡니다.

   ![제안된 테이블.](../media/dataverse-table-proposed.png)

1. **저장 후 종료(Save and exit)** 를 선택한 다음 **저장 후 종료(Save and exit)** 를 다시 선택합니다.

## 연습 2 - 에이전트 만들기

이 연습에서는 자연어를 사용하여 가상 기업의 경비 정책 관련 질문에 답변하는 새 에이전트를 만듭니다.

### 작업 2.1 – 경비 청구 에이전트 만들기

1. `https://copilotstudio.microsoft.com/`의 **Copilot Studio** 홈페이지로 이동합니다.

1. **Copilot Studio** 클래식 환경을 사용하고 있는지 확인합니다. 클래식 환경이 아니면 계속하기 전에 클래식 환경으로 전환합니다.

1. 페이지 위쪽에서 이 연습에 사용할 환경에서 작업 중인지 확인합니다.

1. 왼쪽 탐색 영역에서 **에이전트(Agents)** 를 선택합니다.

1. *에이전트가 수행해야 할 작업을 설명하여 빌드 시작(Start building by describing what your agent needs to do)* 텍스트 상자의 왼쪽 아래에서 **톱니바퀴(Cog)** 이미지로 표시되는 **에이전트 설정(Agent Settings)** 아이콘을 선택합니다.

   ![에이전트 설정 대화 상자의 스크린샷.](../media/agent-settings-dialog.png)

1. 에이전트의 기본 언어를 **영어(미국)(English (United States))** 로 그대로 둡니다.

1. **솔루션(Solution)** 드롭다운에서 **`Lab Exercises`(랩 연습)** 또는 이 연습에 사용할 다른 솔루션을 선택합니다.

1. *스키마 이름(Schema name)* 에 `expenseagent`를 입력합니다.

1. **업데이트(Update)** 를 선택합니다.

1. *에이전트가 수행해야 할 작업을 설명하여 빌드 시작(Start building by describing what your agent needs to do)* 텍스트 상자에 다음 영문 또는 한국어 프롬프트 중 하나를 입력합니다.

   ```prompt
   You are an agent that helps employees with expense claims including questions around expense policy and procedures.
   ```

   ```prompt
   경비 정책과 절차에 관한 질문을 비롯하여 직원의 경비 청구를 지원하는 에이전트입니다.
   ```

1. **보내기(Send)** 아이콘을 선택합니다.

   에이전트 프로비저닝이 완료되면 에이전트 구성을 계속할 수 있습니다.

## 연습 3 - 지식을 기반으로 에이전트 설정

이 연습에서는 에이전트에 지식 원본을 추가하여 에이전트의 답변 기반을 설정합니다.

### 작업 3.1 – 문서를 지식 원본으로 추가

1. 새 브라우저 탭을 열고 `https://github.com/MicrosoftLearning/mslearn-copilotstudio/raw/main/expenses/Expenses_Policy.docx`로 이동한 다음 [경비 정책 문서](https://raw.githubusercontent.com/MicrosoftLearning/mslearn-copilotstudio/main/expenses/Expenses_Policy.docx)를 로컬로 다운로드합니다. 이 문서에는 가상 기업의 경비 정책에 대한 세부 정보가 포함되어 있습니다.

1. 연습 2에서 만든 에이전트가 있는 **Copilot Studio** 브라우저 탭으로 돌아갑니다.

1. **참조 자료(Knowledge)** 탭을 선택하여 에이전트에 정의된 지식 원본을 확인합니다. 현재는 아무것도 없어야 합니다.

   ![Copilot Studio 지식 페이지의 스크린샷.](../media/knowledge-page.png)

1. **+ 참조 자료 추가(+ Add knowledge)** 를 선택하고 에이전트에 추가할 수 있는 여러 유형의 지식 원본을 확인합니다.

   ![Copilot Studio에서 사용할 수 있는 지식 원본의 스크린샷.](../media/knowledge-sources.png)

1. **파일 업로드(Upload file)** 섹션에서 **찾아보기(select to browse)** 를 사용하여 이전에 다운로드한 경비 정책 문서를 업로드하고 **에이전트에 추가(Add to agent)** 를 선택합니다.

   ![Copilot Studio에서 경비 정책 문서를 에이전트의 지식으로 추가하는 스크린샷.](../media/knowledge-add-file.png)

> [!NOTE]
> 파일을 업로드하면 Copilot Studio가 인덱싱을 시작합니다. 이 작업에는 10분 이상 걸릴 수 있으므로 다음 연습을 마친 후 다시 확인합니다.

### 작업 3.2 – 공개 웹 사이트를 참조 자료 원본으로 추가

1. Copilot Studio 에이전트에서 **참조 자료(Knowledge)** 탭을 선택합니다.

1. **+ 참조 자료 추가(+ Add knowledge)** 를 선택합니다.

1. **공개 웹 사이트(Public websites)** 를 선택합니다.

1. **공개 웹 사이트 링크(Public website link)** 텍스트 상자에 `https://www.irs.gov/publications/p463`을 입력합니다. 이 공식 정부 공개 웹 사이트에는 에이전트에 유용할 수 있는 출장 경비 환급 관련 세부 정보가 있습니다.

1. **추가(Add)** 를 선택합니다.

1. **이름(Name)** 에 `Travel, Gift, and Car Expenses | Internal Revenue Service`(출장, 선물 및 자동차 경비 | 미국 국세청)를 입력합니다.

1. **설명(Description)** 에 다음 영문 또는 한국어 값 중 하나를 입력합니다.

   ```prompt
   This knowledge source contains information on reimbursement of travel expenses.
   ```

   ```prompt
   이 지식 원본에는 출장 경비 환급에 관한 정보가 포함되어 있습니다.
   ```

1. **에이전트에 추가(Add to agent)** 를 선택합니다.

> [!NOTE]
> 공개 웹 사이트 인덱싱에는 몇 분이 걸릴 수 있습니다. 응답이 불완전하면 몇 분 기다렸다가 에이전트를 다시 테스트합니다.

### 작업 3.3 – Dataverse 테이블을 지식 원본으로 추가

1. Copilot Studio 에이전트에서 **참조 자료(Knowledge)** 탭을 선택합니다.

1. **+ 참조 자료 추가(+ Add knowledge)** 를 선택합니다.

1. **Dataverse**를 선택합니다.

1. 연습 1에서 만든 **Expenses** 테이블을 검색하여 선택합니다.

   ![Dataverse의 Expenses 테이블을 에이전트의 지식으로 추가하는 스크린샷.](../media/knowledge-add-dataverse.png)

1. **에이전트에 추가(Add to agent)** 를 선택합니다.

   ![Copilot Studio에서 에이전트의 모든 지식 원본을 보여 주는 스크린샷.](../media/knowledge-added.png)

### 작업 3.4 – Dataverse 지식 원본 구성

1. Copilot Studio 에이전트에서 **참조 자료(Knowledge)** 탭을 선택합니다.

1. Dataverse 테이블의 줄임표(**⋮**)를 선택한 다음 **편집(Edit)** 을 선택합니다.

   ![에이전트의 지식 원본을 편집하는 스크린샷.](../media/knowledge-edit.png)

1. **세부 정보(Details)** 탭의 **이름(Name)** 에 **`Expense Claims data`(경비 청구 데이터)** 를 입력합니다.

1. **동의어(Synonyms)** 탭을 선택합니다.

1. **Expense Type** 행에서 **+ 동의어 추가(+ Add synonyms)** 를 선택합니다.

1. `Expense label`을 입력하고 **추가(Add)** 를 선택합니다.

1. `Expense category`를 입력하고 **추가(Add)** 를 선택합니다.

   ![Dataverse 테이블 열에 동의어를 추가하는 스크린샷.](../media/knowledge-synonyms.png)

1. **완료(Done)** 를 선택합니다.

1. **용어집(Glossary)** 탭을 선택합니다.

1. **용어 입력(Enter term)** 에 **`Incidental expenses`(부대 경비)** 를 입력합니다.

1. **설명 입력(Enter description)** 에 다음 영문 또는 한국어 값 중 하나를 입력합니다.

   ```prompt
   Minor, necessary business costs that arise in addition to a primary expense such as tips or fees.
   ```

   ```prompt
   팁이나 수수료와 같은 주요 경비 외에 추가로 발생하는 소액의 필수 비즈니스 비용입니다.
   ```

1. **추가(Add)** 를 선택합니다.

1. **저장(Save)** 을 선택합니다.

### 작업 3.5 – 파일 인덱싱 상태 확인

업로드한 파일의 인덱싱이 완료되었는지 확인합니다. 인덱싱이 아직 진행 중이면 몇 분 기다렸다가 페이지를 새로 고친 후 계속합니다.

1. **참조 자료(Knowledge)** 탭을 선택합니다.

1. 업로드한 파일의 **상태(Status)** 를 확인합니다. 아직 **진행 중(In progress)** 이면 **준비됨(Ready)** 이 될 때까지 몇 분마다 새로 고칩니다.

### 작업 3.6 – 기반 설정 테스트

1. 페이지 오른쪽 위에서 **테스트(Test)** 아이콘을 선택하여 테스트 창을 엽니다.

1. **테스트(Test)** 창에서 변수 **{x}** 아이콘 옆의 줄임표(**...**)를 선택하고 **테스트할 때 활동 맵 표시(Show activity map when testing)** 를 **켬(On)** 으로, **토픽 간 추적(Track between topics)** 을 **끔(Off)** 으로 전환합니다.

   ![활동 맵 표시.](../media/show-activity-map.png)

1. **테스트(Test)** 창 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. 다음 영문 또는 한국어 질문 중 하나를 입력하여 제출합니다.

   ```prompt
   What can I claim for expenses?
   ```

   ```prompt
   어떤 항목을 경비로 청구할 수 있나요?
   ```

1. 응답은 업로드된 경비 정책 문서를 기반으로 해야 하며 구성된 다른 지식 원본을 참조할 수도 있습니다.

   ![대화의 스크린샷.](../media/knowledge-conversation-1.png)

1. **테스트(Test)** 창 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. 다음 영문 또는 한국어 질문 중 하나를 입력합니다.

   ```prompt
   What is the total amount of all expense claims for each category?
   ```

   ```prompt
   각 범주별 모든 경비 청구의 총액은 얼마인가요?
   ```

1. 에이전트는 모든 지식 원본을 검색하고 Dataverse 테이블을 사용하여 응답을 생성해야 합니다.

   ![대화의 스크린샷.](../media/knowledge-conversation-2.png)

1. **테스트(Test)** 창 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. 다음 영문 또는 한국어 질문 중 하나를 입력합니다.

   ```prompt
   What are the limits for incidental expenses?
   ```

   ```prompt
   부대 경비의 한도는 얼마인가요?
   ```

1. 에이전트는 모든 지식 원본을 검색하고 공개 웹 사이트의 정보를 사용하여 응답을 생성해야 합니다.

   ![대화의 스크린샷.](../media/knowledge-conversation-3.png)

## 연습 4 - 생성형 AI 설정

이 연습에서는 에이전트와 생성형 답변 노드의 생성형 AI를 구성합니다.

### 작업 4.1 – 에이전트 지식 설정 구성

1. 에이전트 페이지 오른쪽 위에서 **설정(Settings)** 단추를 선택합니다.

1. **오케스트레이션(Orchestration)** 이 **예 - 응답은 사용 가능한 도구와 참조 자료를 적절히 활용해 동적으로 진행됩니다.(Yes - Responses will be dynamic, using available tools and knowledge as appropriate)** 로 설정되어 있는지 확인합니다.

1. **지식(Knowledge)** 섹션에서 **근거 없는 응답 허용하기(Allow ungrounded responses)** 을 **끔(Off)** 으로 설정합니다.

1. **지식(Knowledge)** 섹션에서 **웹의 정보 사용(Use information from the Web)** 을 **끔(Off)** 으로 설정합니다.

   ![에이전트의 지식 설정 스크린샷.](../media/knowledge-agent-settings.png)

1. **저장(Save)** 을 선택합니다.

1. 설정 페이지 오른쪽 위에서 **X**를 선택하여 설정을 닫습니다.

1. 이전 연습의 프롬프트를 사용하여 에이전트를 테스트합니다. 파일 및 Dataverse 지식 원본은 사용되지만 응답을 생성할 때 공개 웹 사이트는 사용되지 않습니다.

   ```prompt
   What are the limits for incidental expenses?
   ```

   ```prompt
   부대 경비의 한도는 얼마인가요?
   ```

### 작업 4.2 – 생성형 답변 노드 구성

1. **토픽(Topics)** 탭을 선택합니다.

1. **시스템(System)** 토픽으로 필터링합니다.

1. **Conversational boosting** 토픽을 엽니다.

1. **Copilot으로 대화 향상(Boost your conversations with copilots)** 대화 상자가 나타나면 **완료(Done)** 를 선택합니다.

1. **생성형 답변 만들기(Create generative answers)** 노드를 선택합니다.

   ![생성형 답변 노드의 스크린샷.](../media/generative-answers-node.png)

1. **데이터 원본(Data sources)** 아래에서 **편집(Edit)** 을 선택합니다.

1. **선택한 원본만 검색(Search only selected sources)** 을 선택하여 사용하도록 설정합니다.

1. **공개 웹 사이트(Public website)** 지식 원본을 선택합니다.

1. **웹 검색(Web search)** 을 사용하도록 설정합니다.

   **웹 검색(Web search)** 을 사용하도록 설정하면 생성형 답변이 구성된 지식 원본을 공개 웹 정보로 보완할 수 있습니다.
   ![생성형 답변 속성의 스크린샷.](../media/generative-answers-properties.png)

1. **저장(Save)** 을 선택합니다.

1. **개요(Overview)** 탭을 선택합니다.

1. 페이지 오른쪽 위에서 **테스트(Test)** 아이콘을 선택하여 테스트 창을 엽니다.

1. **테스트(Test)** 창에서 변수 **{x}** 아이콘 옆의 줄임표(**...**)를 선택하고 **테스트할 때 활동 맵 표시(Show activity map when testing)** 를 **끔(Off)** 으로, **토픽 간 추적(Track between topics)** 을 **켬(On)** 으로 전환합니다.

1. **테스트(Test)** 창 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. 다음 영문 또는 한국어 질문 중 하나를 입력합니다.

   ```prompt
   What is the current exchange rate between the U.S. dollar and the euro?
   ```

   ```prompt
   현재 미국 달러와 유로의 환율은 얼마인가요?
   ```

1. 지식 원본에서 답변을 제공하지 못하지만 에이전트는 생성형 답변을 사용하여 웹을 검색하고 응답을 생성합니다.

   ![Conversational Boosting 토픽의 대화 스크린샷.](../media/knowledge-conversation-4.png)

### 작업 4.3 – Fallback 토픽

1. **토픽(Topics)** 탭을 선택합니다.

1. **시스템(System)** 토픽으로 필터링합니다.

1. **Conversational boosting** 토픽을 엽니다.

1. **생성형 답변 만들기(Create generative answers)** 노드를 선택합니다.

1. **데이터 원본(Data sources)** 아래에서 **편집(Edit)** 을 선택합니다.

1. **웹 검색(Web search)** 을 사용하지 않도록 설정합니다.

1. **저장(Save)** 을 선택합니다.

1. **개요(Overview)** 탭을 선택합니다.

1. 페이지 오른쪽 위에서 **테스트(Test)** 아이콘을 선택하여 테스트 창을 엽니다.

1. **테스트(Test)** 창에서 변수 **{x}** 아이콘 옆의 줄임표(**...**)를 선택하고 **테스트할 때 활동 맵 표시(Show activity map when testing)**를 **끔(Off)** 으로, **토픽 간 추적(Track between topics)**은 **켬(On)** 으로 설정되어 있는지 확인합니다.

1. **테스트(Test)** 창 위쪽에서 **새 테스트 세션 시작(Start new test session)** 아이콘 **+**를 선택합니다.

1. 다음 영문 또는 한국어 질문 중 하나를 입력합니다.

   ```prompt
   What is the current exchange rate between the U.S. dollar and the euro?
   ```

   ```prompt
   현재 미국 달러와 유로의 환율은 얼마인가요?
   ```

1. 지식 원본과 생성형 답변에서 답변을 제공하지 못합니다. 적합한 기반 응답 또는 생성형 응답이 없으면 대화가 Fallback 토픽으로 라우팅될 수 있습니다.

   ![Fallback 토픽을 사용하는 대화의 스크린샷.](../media/knowledge-conversation-5.png)

## 연습 5 - Microsoft Teams에 에이전트 게시

이 연습에서는 먼저 Microsoft Entra ID 인증이 사용하도록 설정되어 있는지 확인한 후 에이전트를 Microsoft Teams에 게시합니다.

### 작업 5.1 – Microsoft Entra ID 인증

1. 에이전트 페이지 오른쪽 위에서 **설정(Settings)** 단추를 선택합니다.

1. **설정(Settings)** 페이지 왼쪽에서 **보안(Security)** 을 선택합니다.

1. **인증(Authentication)** 을 선택합니다.

1. 아직 선택하지 않았다면 **Microsoft로 인증(Authenticate with Microsoft)** 을 선택합니다.

1. **저장(Save)** 을 선택한 다음 **저장(Save)** 을 다시 선택합니다.

1. **설정(Settings)** 페이지 오른쪽 위에서 **X**를 선택하여 설정을 닫습니다.

### 작업 5.2 – 에이전트 게시

1. 에이전트 페이지에서 **게시(Publish)** 를 선택한 다음 **게시(Publish)** 를 다시 선택하여 확인합니다.

### 작업 5.3 – Microsoft Teams 채널

> [!NOTE]
> 이 랩에서 Teams에 게시하는 작업은 테스트 및 학습을 위한 것입니다. 프로덕션 배포에는 추가 거버넌스, 보안 및 앱 승인 프로세스가 필요할 수 있습니다.

1. **채널(Channels)** 탭을 선택합니다.

   ![Copilot Studio의 채널 탭 스크린샷.](../media/channels-tab-teams.png)

1. **Microsoft 365 및 Microsoft Teams(Microsoft 365 and Microsoft Teams)** 타일을 선택합니다.

1. **Microsoft 365 Copilot에서 에이전트이 사용 가능하도록 설정(Make agent available in Microsoft 365 Copilot)** 을 선택 취소합니다.

1. **채널 추가(Add channel)** 를 선택합니다.

   ![Copilot Studio의 Teams 채널 스크린샷.](../media/channel-teams.png)

1. **Teams에서 에이전트 보기(See agent in Teams)** 를 선택합니다.

1. **이 사이트에서 Microsoft Teams(회사 또는 학교)를 열려고 합니다(This site is trying to open Microsoft Teams (work or school))** 대화 상자에서 **취소(Cancel)** 를 선택합니다.

1. **대신 웹앱 사용(Use the web app instead)** 을 선택합니다.

1. 메시지가 표시되면 Microsoft Teams에 로그인합니다.

1. **추가(Add)** 를 선택하여 Teams에 에이전트를 추가합니다.

   ![Teams에 앱을 추가하는 대화 상자의 스크린샷.](../media/channel-teams-app.png)

1. **열기(Open)** 를 선택하고 Teams에서 에이전트가 로드될 때까지 기다립니다.

1. Microsoft Teams에서 게시된 에이전트를 테스트합니다.

    ![Teams에서 에이전트를 테스트하는 스크린샷.](../media/channel-teams-test.png)

## 요약

이 랩에서는 에이전트에 지식 원본을 추가하고, 지식 원본을 사용하여 프롬프트에 대한 응답을 생성하는 시점과 방식에 생성형 AI 설정이 어떤 영향을 주는지 살펴보았습니다.
