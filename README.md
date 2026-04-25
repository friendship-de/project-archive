# project-archive

Claude Code에서 사용할 수 있는 포트폴리오 케이스 스터디 자동 생성 스킬입니다.  
프로젝트 메모나 Notion 링크를 입력하면 **Problem / Process / Outcome** 구조의 케이스 스터디 초안을 자동으로 작성해줍니다.

## 주요 기능

- 프로젝트 메모 → 케이스 스터디 초안 자동 생성
- Figma 링크 첨부 시 디자인 컨텍스트 자동 추출
- Notion 링크 첨부 시 페이지 내용 자동 읽기
- 품질 체크리스트 및 포트폴리오 리뷰 자동 제공
- Notion 데이터베이스 또는 Markdown 파일로 export

## 설치 방법

### 1. 스킬 파일 복사

```bash
# 개인 스킬 디렉토리에 설치 (모든 프로젝트에서 사용 가능)
cp .claude/skills/archive.md ~/.claude/skills/archive.md

# 또는 특정 프로젝트에만 설치
cp .claude/skills/archive.md [프로젝트 경로]/.claude/skills/archive.md
```

### 2. Notion 연동 설정 (선택)

Notion export 기능을 사용하려면 스킬 파일 내 아래 두 곳을 본인 값으로 교체하세요.

```
YOUR_DATA_SOURCE_ID       → 업무 아카이빙 DB의 data source ID
YOUR_PORTFOLIO_DATABASE_ID → 포트폴리오 저장 DB의 ID
YOUR_WORKSPACE             → Notion 워크스페이스 이름
```

Notion DB ID 확인 방법: Notion 페이지 URL에서 마지막 32자리 문자열이 ID입니다.

```
https://www.notion.so/myworkspace/338f330eead580fdb398edfa1abd0be2
                                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                                   이 부분이 Database ID
```

### 3. 사용하기

Claude Code 터미널에서 아래 명령어를 입력하세요:

```
/archive
```

## 사용 예시

**입력 방법 (아무 형태나 가능):**

```
/archive
```

아래 중 하나 이상을 입력하면 됩니다:
- 자유로운 프로젝트 메모
- Notion 페이지 링크
- Figma 파일 링크

**출력 예시:**

```markdown
# 프로젝트 제목

## Problem
...

## Process
...

## Outcome
...

## Reflection
...
```

작성 후 **Notion 저장** 또는 **Markdown 파일 저장** 옵션을 선택할 수 있습니다.

## Export 옵션

| 옵션 | 설명 |
|------|------|
| A. Notion | 지정한 Notion 데이터베이스에 페이지 자동 생성 |
| B. Markdown | `.md` 파일로 저장 (PDF 변환 가능) |
| C. 수정 요청 | 특정 섹션 수정, 톤 변경, 길이 조절 |

## 요구 사항

- [Claude Code](https://claude.ai/code) 설치 필요
- Figma 연동 시 Figma MCP 서버 인증 필요
- Notion 연동 시 Notion MCP 서버 인증 필요

## 라이선스

MIT
