# PL-7008 한국어 실습 번역 및 유지관리 지침

## 목적

이 디렉터리는 `Instructions`에 있는 영문 콘텐츠의 디렉터리 구조를 그대로 반영한 한국어 번역본을 관리합니다.

- 영문 원본은 수정하지 않습니다.
- 한국어 파일은 영문 원본과 동일한 파일명과 문서 구조를 유지합니다.
- 자연스러운 한국어를 사용하고 필요한 UI 이름은 영문과 함께 표기합니다.
- 영문 원본이 변경되면 이 문서의 동기화 절차에 따라 번역본을 갱신합니다.

## 번역 경로

| 구분 | 경로 |
|---|---|
| 영문 원본 | `Instructions` |
| 한국어 번역 | `Instructions-kr` |
| 영문 미디어 | `Instructions/media` |
| 한국어 미디어 | `Instructions-kr/media` |

## 번역 원칙

- 수행 단계는 `~합니다` 형식으로 작성합니다.
- Microsoft 제품명은 원문을 유지합니다.
- 영어 UI를 사용하는 경우 주요 항목을 `한국어(English)` 형식으로 표기합니다.
- 원문에 없는 절차를 추측하여 추가하지 않습니다.
- 원문의 오류는 임의로 수정하지 않고 알려진 문제로 기록합니다.

## 프롬프트

영문과 한국어 프롬프트를 각각 복사 가능한 `prompt` 코드 블록으로 제공합니다.

````markdown
```prompt
You are an agent that analyzes tasks.
```

```prompt
작업을 분석하는 에이전트입니다.
```
````

- `한국어 의미:`와 같은 레이블을 사용하지 않습니다.
- 한국어 프롬프트 안에 불필요한 Markdown 장식을 넣지 않습니다.
- URL, 자리표시자 및 참조 이름을 보존합니다.

## 사람 친화적인 입력값

실제 영문 입력값은 그대로 유지하고 한국어 설명을 코드 범위 밖에 표기합니다.

```markdown
**`US Benefits Assistant`(미국 복리후생 지원 담당자)**
```

스키마 이름, 변수 이름, 식, 필터, URL, Excel 열 이름 및 종속 선택값에는 이 방식을 적용하지 않습니다.

## 동기화 절차

1. 마지막 동기화 커밋과 현재 원본을 비교합니다.
2. 추가, 삭제, 이름 변경 및 내용 변경을 분류합니다.
3. 영문 diff를 의미 단위로 한국어 문서에 반영합니다.
4. 기존 한국어 파일을 영문 파일로 덮어쓰지 않습니다.
5. 변경된 이미지와 필수 자산을 동일한 상대 경로로 복사합니다.
6. 전체 상대 경로 구조와 링크를 검증합니다.
7. 모든 변경을 반영한 후에만 기준 커밋과 검토일을 갱신합니다.

```powershell
git diff df2bb4d569b0124f866e03a570e426efaad22680..HEAD -- Instructions
python .github\skills\mslearn-korean-localization\scripts\validate_translation.py --repo .
```

## 동기화 상태

| 항목 | 값 |
|---|---|
| 저장소 | `hahaysh/mslearn-copilotstudio-kr` |
| 기준 커밋 | `df2bb4d569b0124f866e03a570e426efaad22680` |
| 마지막 검토일 | `2026-09-27` |

| 파일 | 상태 | 원본 기준 커밋 | 마지막 검토일 |
|---|---|---|---|
| `Labs/00-ILT-setup.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |
| `Labs/01-create-agents.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |
| `Labs/02-manage-topics.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |
| `Labs/03-knowledge.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |
| `Labs/04-workflow-tools.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |
| `Labs/05-create-agent-new-experience.md` | 번역 완료 | `df2bb4d569b0124f866e03a570e426efaad22680` | 2026-09-27 |

## 검증 체크리스트

- [x] 영문과 한국어 파일명이 대응하는가?
- [x] 영문과 한국어 파일의 상대 경로가 대응하는가?
- [x] YAML과 제목 구조가 유지되었는가?
- [x] 단계 번호가 유지되었는가?
- [x] 이미지와 링크 경로가 유지되었는가?
- [x] 참조되는 이미지와 필수 자산이 한국어 디렉터리에 존재하는가?
- [x] 원문의 코드 블록이 보존되었는가?
- [x] 영문과 한국어 프롬프트를 각각 복사할 수 있는가?
- [x] 기술 식별자와 식이 변경되지 않았는가?
- [x] 기존 영문 원본과 관련 없는 파일이 변경되지 않았는가?

## GitHub Pages

기본 공개 URL:

```text
https://<owner>.github.io/<repository>/Instructions-kr/Labs/<lab>.html
```

Pages를 게시한 경우 실제 사이트 URL과 확인 결과를 이 섹션에 기록합니다.

## 알려진 원문 문제

- `Labs/05-create-agent-new-experience.md`는 미리 빌드된 작업을 추가한다고 설명하지만 작업을 명시적으로 추가하고 구성하는 단계가 보이지 않습니다.
- `Labs/05-create-agent-new-experience.md` 요약의 `Lab 03` 참조는 현재 파일 순서의 워크플로 실습과 일치하지 않을 수 있습니다.
- `Labs/03-knowledge.md`의 경비 정책 문서 URL은 현재 저장소가 아니라 MicrosoftLearning 원본 저장소를 가리킵니다.
