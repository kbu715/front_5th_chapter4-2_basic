## 성능 개선 보고서

### 0. 배포 URL

https://front-5th-chapter4-2-basic-blond.vercel.app/

### 1. 개선 이유

서비스 초기 로딩 속도 및 사용자 경험을 저해하는 요소들이 Lighthouse 및 웹 성능 분석 도구를 통해 발견되었습니다. 주요 이슈는 다음과 같습니다:

- 불필요하거나 지연 가능한 스크립트의 초기 로딩
- 주요 이미지의 lazy loading 적용으로 인한 렌더링 지연
- SEO 및 접근성 점수 저하 (meta 정보 누락, heading 구조 오류 등)
- 이미지 용량 과다
- 레이아웃 시프트로 인한 CLS 점수 저하

---

### 2. 개선 방법

#### ✅ 이미지 리소스 최적화

- `png`, `jpg` → `webp` 변환 및 적용
- `img` 태그에 `width`, `height` 명시
- `picture` 태그 활용하여 디바이스별 이미지 대응
- 불필요 이미지 삭제
- Hero 이미지 lazy loading 제거 및 preload 처리

#### ✅ JS / CSS 로딩 최적화

- Google Fonts를 `.woff2` 파일로 변환 후 자체 정적 호스팅
- 일부 스크립트에 `async`, `defer` 적용
- 사용되지 않는 스타일 / 스크립트 제거
- 필요한 스크립트는 지연 로딩 처리

#### ✅ 이벤트 및 레이아웃 개선

- 기기별(hero 이미지) preload 조건 분기 처리
- `all-products` 영역 레이아웃 시프트 최소화

#### ✅ 접근성 및 SEO 개선

- heading 순서 재구성 (접근성 점수 개선)
- 주요 meta 태그 추가
- 이미지에 alt 속성 추가

---

### 3. 개선 후 향상된 지표 (Pagespeed Insights 기준)

| 항목                          | 개선 전 | 개선 후   |
| ----------------------------- | ------- | --------- |
| Performance                   | 62      | **99**    |
| Accessibility                 | 84      | **93**    |
| Best Practices                | 79      | **96**    |
| SEO                           | 70      | **100**   |
| CLS (Cumulative Layout Shift) | 0.48    | **0.001** |

---
<img width="985" alt="스크린샷 2025-06-05 오후 4 04 11" src="https://github.com/user-attachments/assets/31916e04-e975-4ba8-b95e-ea25a4b1c6e7" />

<img width="950" alt="스크린샷 2025-06-05 오후 4 04 29" src="https://github.com/user-attachments/assets/85a172ca-b44d-4b61-8dc0-892ceb633be2" />

