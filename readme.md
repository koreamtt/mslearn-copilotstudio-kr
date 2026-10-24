# Microsoft Copilot Studio 한국어 실습

PL-7008 Microsoft Copilot Studio 실습 가이드를 제공하는 `koreamtt/mslearn-copilotstudio-kr` 저장소입니다.

## 온라인 실습 가이드

**<https://koreamtt.github.io/mslearn-copilotstudio-kr/>**

## 프로젝트 구조

| 경로 | 역할 |
|---|---|
| [Instructions/Labs](Instructions/Labs/) | 영문 원본 실습 6개 |
| [Instructions-kr/Labs](Instructions-kr/Labs/) | 원본과 대응하는 한국어 번역 6개 |
| [Instructions-kr/Labs2](Instructions-kr/Labs2/) | 홈페이지에서 제공하는 한국어 실습 6개와 실습별 이미지 |
| [Instructions-kr/media](Instructions-kr/media/) | 원본 대응 번역에서 사용하는 이미지 |
| [Allfiles](Allfiles/), [expenses](expenses/) | 실습용 다운로드 파일 |
| [index.md](index.md) | `Instructions-kr/Labs2/`의 실습 목록을 자동 생성하는 홈페이지 |
| [_config.yml](_config.yml) | Jekyll 테마, 사이트 주소 및 저장소 정보 |
| [_build.yml](_build.yml) | 원본에서 상속된 Azure Pipelines 문서 패키징 설정. GitHub Pages 게시에는 사용하지 않음 |

## GitHub Pages 운영

- 게시 방식: **Deploy from a branch** (`legacy`), **main** 브랜치, **/(root)**.
- `main`에 변경사항을 푸시하면 GitHub Pages가 Jekyll 테마로 사이트를 빌드합니다.
- 실습 주소: `https://koreamtt.github.io/mslearn-copilotstudio-kr/Instructions-kr/Labs2/<lab>.html`.
- 내부 실습 링크는 Jekyll의 `relative_url` 필터로 프로젝트 경로를 반영합니다.
- 조직명이나 저장소명이 바뀌면 [_config.yml](_config.yml)의 `url`, `baseurl`, `repository`, `github_username`과 이 문서의 사이트 주소를 함께 갱신합니다.

번역 기준과 동기화 절차는 [한국어 번역 유지관리 지침](Instructions-kr/README.md)을 참고합니다. `Labs2`는 별도 편집본이므로 영문 원본과 일대일 비교하는 전체 번역 검증에서는 추가 경로로 보고됩니다. 원본 대응 번역의 `04-workflow-tools.md`에는 인라인 코드 순서 검증 오류가 있습니다.

## 원본 프로젝트 안내

### Copilot Studio Exercises

**Are you an MCT?** - Have a look at our [GitHub User Guide for MCTs](https://microsoftlearning.github.io/MCT-User-Guide/)

This repository contains lab exercises for modules on Microsoft Learn and in Microsoft instructor-led training courses.

### How do I contribute?

- Any MCT (Microsoft Certified Trainer) can submit a pull request to the code or content in the GitHub repro. Microsoft and the course author will then triage and include content and lab code changes as needed.

- You can submit bugs, changes, improvement, and ideas. 
