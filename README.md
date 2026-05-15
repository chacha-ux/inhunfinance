# 청소년 금융교육 길잡이 — 사이트 자료

이 폴더에 들어있는 파일은 GitHub Pages로 배포할 수 있는 **Jekyll 정적 사이트**입니다. 손제연 교수의 DeepWrite 사이트와 동일한 `Just the Docs` 테마를 사용합니다.

---

## 📁 폴더 구조

```
site/
├─ _config.yml       ← 사이트 설정 (제목, 검색, 테마 등)
├─ Gemfile           ← Jekyll 의존성 (로컬 빌드 시 필요)
├─ .gitignore        ← GitHub에 올리지 않을 파일
├─ index.md          ← 홈 (사이트 소개)
├─ fraud.md          ← 금융 사기 챕터
├─ products.md       ← 금융 상품 챕터
├─ resources.md      ← 참고 사이트 챕터
└─ README.md         ← 이 파일
```

---

## 🚀 GitHub Pages에 올리기 (처음 한 번)

### 1단계 — GitHub 계정 만들기

[github.com](https://github.com) 에서 무료 계정 생성. 이미 있으면 그대로 사용.

### 2단계 — 저장소 만들기

- 우측 상단 `+` → **New repository**
- **Repository name**: 원하는 이름 (예: `finance-edu`, `inheon-finance` 등)
  - 만약 이름을 `여러분의계정명.github.io` 로 만들면 주소가 `https://여러분의계정명.github.io` 가 됨
  - 다른 이름이면 주소가 `https://여러분의계정명.github.io/저장소이름` 이 됨
- **Public** 선택 (Private 저장소는 GitHub Pages 무료 사용 불가)
- 나머지는 기본값으로 두고 **Create repository**

### 3단계 — 파일 업로드

방법 A. **드래그&드롭 (가장 쉬움)**

1. 방금 만든 저장소 페이지에서 **uploading an existing file** 링크 클릭
2. 이 폴더의 모든 파일 (`_config.yml`, `index.md`, `fraud.md`, `products.md`, `resources.md`, `Gemfile`, `.gitignore`) 을 한꺼번에 드래그
3. 페이지 하단에서 **Commit changes** 클릭

방법 B. **Git 명령어**

```bash
git clone https://github.com/여러분의계정명/저장소이름.git
# 이 폴더의 파일들을 clone된 폴더로 복사
git add .
git commit -m "Initial site"
git push
```

### 4단계 — Pages 활성화

1. 저장소 페이지 상단의 **Settings** 클릭
2. 좌측 메뉴에서 **Pages** 클릭
3. **Source**: `Deploy from a branch` 선택
4. **Branch**: `main` (또는 `master`), 폴더는 `/ (root)` 선택
5. **Save** 클릭
6. 1~2분 후 페이지 상단에 사이트 주소가 표시됨

### 5단계 — baseurl 설정 (저장소 이름이 `username.github.io` 가 아닌 경우)

`_config.yml` 파일을 열어서 `baseurl: ""` 부분을 저장소 이름으로 바꿔주세요.

```yaml
# 예: 저장소 이름이 finance-edu 라면
baseurl: "/finance-edu"
```

수정 후 commit 하면 자동으로 다시 배포됩니다.

---

## ✏️ 내용 수정하기

### 가장 쉬운 방법 — GitHub 웹에서 직접 편집

1. 저장소에서 수정할 파일 클릭 (예: `fraud.md`)
2. 우측 상단의 **연필 아이콘** ✏️ 클릭
3. 텍스트 수정
4. 수정 중 상단의 **Preview** 탭을 누르면 결과 미리보기 가능
5. 페이지 하단의 **Commit changes** 클릭
6. 1~2분 후 사이트에 반영됨

### 마크다운 기본 문법 5가지

```markdown
# 큰 제목
## 중간 제목
### 작은 제목

**굵게**
*기울임*

- 목록 항목 1
- 목록 항목 2

[링크 표시 텍스트](https://example.com)

![이미지 설명](https://이미지주소.jpg)
```

이게 전부입니다. 이 사이트의 모든 페이지도 이 정도 문법으로 작성되어 있어요.

### 이미지 추가하기

#### 방법 1: 외부 이미지 URL 사용 (간단)

```markdown
![설명](https://이미지의URL.jpg)
```

#### 방법 2: 저장소에 이미지 업로드

1. 저장소에 `assets/images/` 폴더 만들기
2. 그 폴더에 이미지 파일 업로드
3. 마크다운에서 다음과 같이 참조

```markdown
![설명](/assets/images/내이미지.png)
```

`baseurl` 을 사용했다면:

```markdown
![설명]({{ site.baseurl }}/assets/images/내이미지.png)
```

### 페이지 순서 바꾸기

각 페이지 상단의 frontmatter에 있는 `nav_order` 숫자를 바꾸면 됩니다.

```yaml
---
title: 금융 사기
nav_order: 2     ← 이 숫자가 작을수록 사이드바 위쪽에 표시됨
---
```

### 새 챕터 추가하기

1. 새 마크다운 파일 만들기 (예: `quiz.md`)
2. 상단에 frontmatter 추가:

```yaml
---
layout: default
title: 퀴즈
nav_order: 5
permalink: /quiz/
---
```

3. 그 아래에 내용 작성
4. Commit

---

## 🌐 로컬에서 미리보기 (선택)

수정 후 사이트에 어떻게 보일지 자기 컴퓨터에서 미리 확인하고 싶다면:

```bash
# Ruby와 Bundler가 설치되어 있어야 함
bundle install
bundle exec jekyll serve
# 브라우저에서 http://localhost:4000 으로 접속
```

이건 선택사항이고, GitHub에 직접 올려도 확인 가능합니다.

---

## 🆘 문제가 생겼다면

- **사이트가 안 떠요**: `_config.yml` 의 `baseurl` 이 저장소 이름과 일치하는지 확인하세요.
- **링크가 깨져요**: 페이지 간 링크는 `/fraud/` 처럼 절대 경로로 쓰는 게 안전합니다.
- **변경사항이 안 보여요**: GitHub Pages는 빌드에 1~2분 걸립니다. 새로고침 후 잠시 기다려보세요.
- **검색이 안 돼요**: `_config.yml` 의 `search_enabled: true` 가 설정되어 있는지 확인하세요.
- **테마가 적용 안 돼요**: `_config.yml` 의 `remote_theme: just-the-docs/just-the-docs` 부분을 확인하세요.

---

## 📜 라이선스 / 출처

본 자료는 **서울대학교 글로벌사회공헌단** 사회공헌활동의 일환으로, 인헌중학교 학생들을 위해 멘토단이 직접 제작했습니다.

본문에 인용된 외부 자료의 저작권은 각 출처에 있으며, 본 사이트는 교육 목적으로 출처를 표기하여 안내하고 있습니다.
