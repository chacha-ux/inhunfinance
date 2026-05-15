# 청소년 금융교육 길잡이 — 사이트 자료 (수정본)

## ⚠️ 이전 버전에서 무엇이 바뀌었나

이전 버전이 작동하지 않은 원인을 고쳤습니다.

1. **`_config.yml`의 `baseurl`** 을 `/inhunfinance` 로 설정 → 테마의 CSS·JS·아이콘이 제대로 로드됨
2. **모든 내부 링크**에 Jekyll의 `relative_url` 필터를 적용 → 어떤 baseurl 환경에서도 안 깨짐

저장소(`chacha-ux/inhunfinance`)에 이 폴더의 파일들을 **그대로 덮어쓰기** 하면 정상화됩니다.

---

## 📁 폴더 구조

```
site/
├─ _config.yml       ← baseurl: "/inhunfinance" 로 설정됨
├─ Gemfile
├─ .gitignore
├─ index.md          ← 홈
├─ fraud.md          ← 금융 사기
├─ products.md       ← 금융 상품
├─ resources.md      ← 참고 사이트
└─ README.md         ← 이 파일
```

---

## 🔄 덮어쓰기 절차

### 방법 A — GitHub 웹에서 (가장 쉬움)

1. [chacha-ux/inhunfinance 저장소](https://github.com/chacha-ux/inhunfinance) 로 이동
2. 기존 파일 6개(`_config.yml`, `index.md`, `fraud.md`, `products.md`, `resources.md`, `Gemfile`, `.gitignore`)를 각각 클릭 → 휴지통 아이콘으로 삭제하거나, 그대로 둬도 됨
3. **Add file → Upload files** 클릭
4. 이 폴더의 모든 파일을 한꺼번에 드래그
5. 같은 이름이 있으면 **Replace** 확인
6. 페이지 하단의 **Commit changes** 클릭
7. **1~2분 대기 후** `https://chacha-ux.github.io/inhunfinance/` 새로고침

### 방법 B — Git 명령어

```bash
git clone https://github.com/chacha-ux/inhunfinance.git
# 이 폴더의 파일들로 덮어쓰기
git add .
git commit -m "Fix baseurl and internal links"
git push
```

---

## ✅ 정상 작동 확인

`https://chacha-ux.github.io/inhunfinance/` 를 새로고침했을 때 다음이 보여야 정상:

- 좌측에 **사이드바**(홈, 금융 사기, 금융 상품, 참고 사이트 메뉴)
- 상단에 **검색창**
- **깔끔한 폰트** (system-ui 또는 sans-serif)
- 아이콘이 **작은 크기**로 표시
- 페이지 간 링크 클릭 시 **정상 이동** (404 없음)

만약 여전히 깨져 보인다면:
- 브라우저 캐시를 비우고 새로고침 (Mac: ⌘+Shift+R / Windows: Ctrl+Shift+R)
- GitHub Pages가 새 빌드를 완료할 때까지 1~2분 더 기다리기

---

## ✏️ 앞으로 내용을 수정하려면

### GitHub 웹에서 편집

1. 저장소에서 수정할 파일 클릭 (예: `fraud.md`)
2. 우측 상단의 **연필 아이콘** ✏️ 클릭
3. 텍스트 수정
4. 상단의 **Preview** 탭으로 미리 확인 가능
5. **Commit changes** 클릭
6. 1~2분 후 사이트에 반영

### 마크다운 기본 문법

```markdown
# 큰 제목
## 중간 제목
### 작은 제목

**굵게**

- 목록 1
- 목록 2

[링크 표시 텍스트](https://example.com)

![이미지 설명](https://이미지주소.jpg)
```

### 사이트 내부 페이지로 링크 걸기

다른 챕터로 링크를 걸 때는 **반드시 `relative_url` 필터**를 사용하세요. 그래야 baseurl이 바뀌어도 안 깨집니다.

```markdown
[금융 사기 챕터]({% raw %}{{ '/fraud/' | relative_url }}{% endraw %})
[금융 상품 챕터]({% raw %}{{ '/products/' | relative_url }}{% endraw %})
[참고 사이트 챕터]({% raw %}{{ '/resources/' | relative_url }}{% endraw %})
```

### 이미지 추가

1. 저장소에 `assets/images/` 폴더 만들고 이미지 업로드
2. 마크다운에서 다음과 같이 참조

```markdown
![설명]({% raw %}{{ '/assets/images/내이미지.png' | relative_url }}{% endraw %})
```

---

## 🆘 그래도 안 되면

- 새로고침: **Ctrl/⌘ + Shift + R**
- GitHub의 **Settings → Pages** 에서 빌드 상태 확인 (녹색 체크가 떠야 함)
- 저장소의 **Actions** 탭에서 빌드 에러 메시지 확인
