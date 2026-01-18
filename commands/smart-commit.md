---
description: Smart commit with auto-generated commit message and push
allowed-tools: Read, Bash(git:*)
argument-hint: [optional commit type: feat|fix|docs|refactor|style|chore|test]
---

# Smart Commit Command

변경사항을 분석하여 적절한 커밋 메시지를 자동 생성하고 커밋 및 푸시를 수행합니다.

## Step 1: 변경사항 확인

먼저 현재 git 상태를 확인합니다:

!`git status`

변경사항이 없으면 "커밋할 변경사항이 없습니다"라고 알리고 종료합니다.

## Step 2: 변경사항 분석

변경된 파일 목록과 상태를 확인합니다:

!`git diff --name-status`

변경 통계를 확인합니다:

!`git diff --stat`

변경된 파일들의 주요 변경 내용을 확인하기 위해 `git diff`를 실행합니다:

!`git diff`

## Step 3: 커밋 메시지 생성

변경사항을 분석하여 적절한 커밋 메시지를 생성합니다.

### 커밋 타입 결정 규칙:

- **feat**: 새로운 기능 추가 (새 파일 추가, 기능 확장)
- **fix**: 버그 수정 (에러 수정, 문제 해결)
- **docs**: 문서 수정 (README, 주석, 문서 파일)
- **refactor**: 코드 리팩토링 (기능 변경 없이 코드 구조 개선)
- **style**: 코드 포맷팅 (들여쓰기, 세미콜론 등 스타일만 변경)
- **chore**: 빌드/설정 변경 (의존성, 설정 파일)
- **test**: 테스트 코드 추가/수정

### 메시지 생성 기준:

1. 변경된 파일의 경로와 이름 분석
2. 변경 내용의 성격 파악 (추가/수정/삭제)
3. 주요 변경사항 요약
4. 타입 결정 (인자로 타입이 제공되면 `$1` 사용, 없으면 분석 결과 사용)

### 메시지 형식:

```
[타입] 간단한 설명

- 주요 변경사항 1
- 주요 변경사항 2
- 변경된 파일: file1, file2, ...
```

## Step 4: 커밋 및 푸시

생성된 커밋 메시지로 커밋하고 푸시합니다:

!`git add -A`

커밋 메시지는 위에서 생성한 내용을 사용합니다. 메시지에 특수문자가 포함되어 있으면 적절히 이스케이프 처리합니다.

!`git commit -m "[생성된 커밋 메시지]"`

푸시를 실행합니다:

!`git push`

푸시 결과를 확인하고, 실패 시 에러 메시지를 표시합니다.

## 실행 순서 요약

1. `git status`로 변경사항 확인
2. 변경사항이 없으면 종료
3. `git diff --name-status`와 `git diff --stat`으로 변경 파일 분석
4. `git diff`로 변경 내용 확인
5. 변경사항을 분석하여 커밋 메시지 생성
6. `git add -A`로 스테이징
7. 생성된 메시지로 `git commit`
8. `git push`로 푸시
9. 결과 확인 및 보고
