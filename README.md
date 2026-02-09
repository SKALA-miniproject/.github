# 🚀 Organization Git 협업 가이드

이 레포지토리(`.github`)는 우리 Organization의 **기본 Issue/PR 템플릿**과 협업 규칙(표준)을 관리합니다. 모든 프로젝트 레포지토리는 아래 규칙에 따라 **브랜치 → PR → 리뷰 → 머지** 흐름으로 진행합니다.



## 1) 기본 원칙

### Default Branch

* 기본 브랜치: **`main`**

### main 브랜치 보호 규칙

* `main`에는 **직접 push 금지**
* `main` 반영은 **Pull Request(PR)로만** 가능
* PR은 **승인 1명 필수**
* PR 내 리뷰 코멘트/대화는 **Resolve(해결) 후** 머지 가능



## 2) 이슈(Issue) 사용 규칙

이슈는 다음 중 하나로 작성합니다.

* **Feature**: 기능 추가/변경
* **Bug**: 버그 제보/수정
* **Blank**: 논의/메모/조사 등 자유 이슈

**권장 흐름:**

1. 작업 시작 전 **이슈를 먼저 생성**
2. 이슈 번호를 기준으로 브랜치 생성
3. PR에서 이슈를 연결해 자동 종료



## 3) 브랜치 네이밍 규칙 (권장)

이슈 번호를 포함해 브랜치명을 통일합니다.

* `feat/<이슈번호>-요약`
* `fix/<이슈번호>-요약`
* `chore/<이슈번호>-요약`
* `docs/<이슈번호>-요약`

**예시:**

* `feat/12-queue-eta`
* `fix/34-payment-dup`
* `chore/7-config-cleanup`



## 4) PR 규칙

### PR 제목 규칙 (필수)

PR 제목은 아래 형식으로 작성합니다.

> `feat|fix|chore|docs: 요약 (#이슈번호)`

* **예시**: `feat: 대기열 ETA 표시 (#12)`

### PR 본문 규칙 (필수)

PR 본문에 아래 문구를 포함하여 이슈를 연결합니다.

> `Closes #<이슈번호>`

* **예시**: `Closes #12` (머지 시 해당 이슈 자동 종료)



## 5) 커밋 메시지 규칙 (권장)

권장 커밋 메시지 형식:

> `feat|fix|chore|docs: 요약 (#이슈번호)`

**예시:**

```bash
git commit -m "feat: 대기열 ETA API 추가 (#12)"

```

*※ 초기 세팅 등 이슈가 없는 작업은 `(#이슈번호)` 생략 가능*



## 6) 표준 작업 흐름

### 6-1) 레포 클론 (처음 1회)

```bash
git clone <레포주소>
cd <레포폴더>

```

### 6-2) main 최신화 (작업 시작 전)

```bash
git checkout main
git pull origin main

```

### 6-3) 브랜치 생성

```bash
git checkout -b feat/12-queue-eta

```

### 6-4) 작업 후 커밋

```bash
git status          # 변경 파일 확인
git add .           # 스테이징
git commit -m "feat: 대기열 ETA API 추가 (#12)"

```

### 6-5) 브랜치 푸시

```bash
# 처음 푸시 시 -u 옵션 포함
git push -u origin feat/12-queue-eta

```

### 6-6) PR 생성 및 리뷰

1. GitHub에서 **Compare & pull request** 클릭
2. **PR 제목 규칙** 준수 여부 확인
3. PR 본문에 **`Closes #이슈번호`** 포함
4. 리뷰어 지정 및 승인 대기
5. **승인 1명 + 모든 코멘트 Resolve** 확인 후 머지

### 6-7) 머지 후 로컬 정리 (권장)

```bash
git checkout main
git pull origin main
git branch -d feat/12-queue-eta # 로컬 브랜치 삭제

```


## 7) 자주 하는 실수 체크 (⚠️)

* [ ] `main` 브랜치에서 직접 작업/커밋함 (항상 브랜치 생성 후 작업하세요!)
* [ ] PR 제목에 `(#이슈번호)`를 누락함
* [ ] PR 본문에 `Closes #이슈번호`를 누락해 이슈가 자동으로 닫히지 않음
* [ ] 리뷰 코멘트를 Resolve하지 않고 머지를 시도함
