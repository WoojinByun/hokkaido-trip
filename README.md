# 홋카이도 공항 선택지 비교

홋카이도 여행 A/B/C안의 항공, 숙소, 이동 구간을 비교하는 정적 페이지입니다. GitHub Pages로 배포하며, 페이지 내용은 암호로 보호됩니다.

## 구성

- `index.html`: 비밀번호 입력 화면과 암호화된 페이지 내용입니다. 직접 편집하지 않고 빌드로 만듭니다.
- `data/*.geojson`: 지도 배경 데이터입니다. 평문으로 공개됩니다.
- 원본 페이지와 일정 데이터는 저장소 밖 `site-src/`에 있으며 저장소에 올리지 않습니다.

## 빌드

`site-src/`는 저장소 밖에 있습니다. 일정 JSON과 원본 페이지를 고친 뒤 다음을 실행합니다.

```
SITE_PASSWORD='<비밀번호>' node site-src/build.mjs
```

빌드는 `site/index.html`을 다시 씁니다. 비밀번호는 파일에 적지 않습니다.

## 로컬 미리보기

```
cd site
python3 -m http.server 8000
```

http://localhost:8000 을 엽니다. 비밀번호 화면에서 암호를 입력하면 내용이 표시됩니다.

## 데이터 갱신

1. `python3 artifact/compare/gen_data.py`로 일정 JSON을 만듭니다.
2. 생성된 `itinerary-*.json`을 `site-src/data/`로 복사합니다.
3. 위 빌드 명령을 실행합니다.
4. 변경을 커밋하고 push합니다.

## 지도

- 구글 지도 탭: 구글 지도 임베드를 씁니다. API 키가 필요 없습니다.
- 간단 지도 탭: Leaflet으로 그린 지도입니다. 배경 타일은 쓰지 않습니다.
