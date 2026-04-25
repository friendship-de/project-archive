# project-archive

Claude Code에서 사용할 수 있는 포트폴리오 케이스 스터디 자동 생성 스킬입니다.  
프로젝트 메모나 Notion 링크를 입력하면 **Problem / Process / Outcome** 구조의 케이스 스터디 초안을 자동으로 작성해줍니다.

## 주요 기능

- 프로젝트 메모 → 케이스 스터디 초안 자동 생성
- 초안 작성 전 빠진 맥락만 골라 사전 질문 (최대 3개)
- Figma 링크 첨부 시 디자인 컨텍스트 자동 추출
- Notion 링크 첨부 시 페이지 내용 자동 읽기
- JD(채용공고) 첨부 시 해당 회사 기준으로 강조점 자동 조정
- 품질 체크리스트 및 포트폴리오 리뷰 자동 제공
- Notion 데이터베이스 또는 Markdown 파일로 export
- 포트폴리오 전체 일관성 감사 (`/archive audit`)

## 전체 명령어

| 명령어 | 설명 |
|--------|------|
| `/archive` | 케이스 스터디 자동 생성 |
| `/archive setup` | 사용자 프로필 최초 설정 (1회) |
| `/archive jd:[링크 또는 텍스트]` | JD 기반 맞춤 버전 생성 |
| `/archive audit` | 저장된 케이스 스터디 전체 감사 |

## 설치 방법

### 1. 스킬 파일 복사

모든 프로젝트에서 공통으로 사용하려면 **개인 스킬 디렉토리**에 설치합니다.

```bash
# 개인 스킬 디렉토리 생성 (없는 경우)
mkdir -p ~/.claude/skills

# 스킬 파일 복사 (모든 프로젝트에서 사용 가능)
cp .claude/skills/archive.md ~/.claude/skills/archive.md
```

특정 프로젝트에만 설치하려면:

```bash
cp .claude/skills/archive.md [프로젝트 경로]/.claude/skills/archive.md
```

### 2. 프로필 설정 (권장)

스킬 설치 후 아래 명령으로 프로필을 한 번 설정해두면 이후 케이스 스터디마다 역할·도구·협업 방식이 자동 반영됩니다.

```
/archive setup
```

프로필 파일은 `~/.claude/skills/archive-profile.md`에 저장됩니다.  
Notion 연동을 사용하려면 이 파일의 Notion 설정 항목에 실제 ID를 입력하세요.

```
YOUR_DATA_SOURCE_ID        → 업무 아카이빙 DB의 data source ID
YOUR_PORTFOLIO_DATABASE_ID → 포트폴리오 저장 DB의 ID
YOUR_WORKSPACE             → Notion 워크스페이스 이름
```

Notion DB ID 확인 방법: Notion 페이지 URL의 마지막 32자리 문자열이 ID입니다.

```
https://www.notion.so/myworkspace/338f330eead580fdb398edfa1abd0be2
                                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                                   이 부분이 Database ID
```

### 3. MCP 서버 연결 (선택)

| 연동 | 필요한 MCP 서버 |
|------|----------------|
| Notion 자동 읽기/저장 | Notion MCP |
| Figma 디자인 컨텍스트 추출 | Figma MCP |

## 사용 흐름

```
1. /archive setup       → 프로필 설정 (최초 1회)
2. /archive             → 케이스 스터디 생성
3. /archive jd:[링크]   → JD 맞춤 버전 생성 (지원할 때마다)
4. /archive audit       → 포트폴리오 전체 점검 (케이스가 쌓이면)
```

## 출력 구조

```markdown
# 프로젝트 제목

## Overview
역할 / 기간 / 팀 구성 / 사용 도구 / 프로젝트 유형

## Problem
## AS-IS → TO-BE
## Process
## Outcome
## Reflection
```

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
