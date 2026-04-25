# 🇳🇱 네덜란드 여행 큐레이션

암스테르담과 1시간 이내 권역의 관광지·사회연대경제 기업·맛집 132곳 큐레이션.
필터·검색·즐겨찾기·지도·자동 이미지 로딩을 지원하는 단일 HTML 인터랙티브 가이드.

## 🚀 Vercel 배포

### 방법 1: Git 연동 (추천)

1. 이 저장소를 본인 GitHub 계정으로 fork 또는 import
2. [vercel.com/new](https://vercel.com/new) 접속
3. **Import Git Repository** → 이 저장소 선택
4. Framework Preset: **Other** (자동 감지됨)
5. **Deploy** 클릭 → 30초~1분 후 배포 완료

### 방법 2: Vercel CLI

```bash
npm i -g vercel
vercel
```

## 🗺 Naver Maps API 연결

1. [console.ncloud.com](https://console.ncloud.com) 가입 + 결제카드 등록
2. **Services → Application Service → Maps** → Application 등록
3. **Web Dynamic Map** 서비스 활성화
4. **Web 서비스 URL**에 배포된 도메인 등록 (예: `https://your-project.vercel.app`)
5. 발급된 **Client ID** (32자리) 복사
6. `index.html` 상단 주석을 찾아서:

```html
<!-- 변경 전 (주석 처리됨) -->
<!--
<script src="https://oapi.map.naver.com/openapi/v3/maps.js?ncpKeyId=YOUR_CLIENT_ID"></script>
-->
```

```html
<!-- 변경 후 (주석 풀고 실제 키 입력) -->
<script src="https://oapi.map.naver.com/openapi/v3/maps.js?ncpKeyId=발급받은_실제_32자리_키"></script>
```

7. GitHub에 push → Vercel이 자동 재배포

## ✨ 기능

- **필터링**: 카테고리 (관광지·사회연대경제·맛집) × 도시 (7개 권역) × 키워드 검색
- **즐겨찾기**: ★ 클릭으로 픽 추가, 픽 목록 텍스트 복사 가능
- **지도 연동**: Naver Maps 마커 자동 생성, 카드 ↔ 마커 양방향 클릭 동기화
- **자동 이미지**: 위키피디아 REST API에서 각 장소 대표 이미지를 lazy load
- **반응형**: 데스크톱·태블릿·모바일 모두 대응
- **인쇄용 스타일**: 종이로 출력해도 깔끔

## 📁 구조

```
.
├── index.html          # 단일 파일 - 모든 데이터·스타일·로직 포함
├── README.md           # 이 파일
├── vercel.json         # Vercel 설정 (캐시 헤더 등)
└── .gitignore
```

## 🛠 로컬 미리보기

CORS 정책 때문에 `file://` 직접 열기는 권장하지 않습니다. 간단한 로컬 서버:

```bash
# Python 3
python3 -m http.server 8000

# 또는 Node.js
npx serve .
```

그 후 `http://localhost:8000`으로 접속.

## 📝 데이터 출처

- I Amsterdam · Visit Haarlem · ImpactCity Den Haag · Social Impact Factory · Amsterdam Impact
- 이미지: Wikipedia / Wikimedia Commons (REST API 자동 로드)
- 위경도는 일부 근사값 포함 — 정확한 위치는 각 카드의 구글맵 링크 참조

## 📜 라이선스

데이터·콘텐츠는 개인 여행 참고용으로 자유롭게 사용 가능. 코드는 MIT.
