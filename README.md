# 위성영상 × AI 실습: 2025 의성 산불 피해 분석

환경공간정보 활용 청년인재 역량 강화교육 · 2026.10.08 · 국립공주대학교 산림과학과
경희대학교 김은빈 (ebkim@khu.ac.kr)

Sentinel-2 위성영상으로 2025년 의성 산불 피해를 지수(NDVI·NBR·dNBR)로 계산하고, 발화 후 영상 한 장으로 피해를 찾는 AI(MLP·U-Net)를 직접 학습해 본다. Google Colab과 Google Earth Engine에서 실행한다.

## Colab에서 열기

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ebkim0925/2026_Kongju_GeoAI/blob/main/uiseong_wildfire_handson.ipynb)

위 버튼을 누르면 Colab에서 노트북이 열린다. 내 계정에 저장하려면 **파일 → 드라이브에 사본 저장**을 누른다.

## 수업 전에 준비할 것

1. **Google 계정** (Gmail). 없으면 만들고, 휴대폰 인증을 준비한다.
2. **Earth Engine 등록**
   - https://earthengine.google.com 에서 **비영리(Noncommercial)** 용도로 등록한다.
   - Google Cloud 프로젝트를 하나 만들고 **프로젝트 ID**를 적어 둔다.
   - 결제 계정 화면이 나오면 **Community** 등급(무료)을 고른다.
3. 개인 노트북(PC)

## 실습을 시작할 때

1. 위 **Open In Colab** 버튼 → **파일 → 드라이브에 사본 저장**
2. **런타임 → 런타임 유형 변경 → T4 GPU**
3. 섹션 2의 `EE_PROJECT = ""` 따옴표 안에 본인 프로젝트 ID를 넣는다.
4. **런타임 → 모두 실행**. 인증 창이 뜨면 허용한다.

## 실습 순서 (110분)

| 단계 | 시간 | 내용 |
|---|---|---|
| 1. 준비 | 10분 | Colab 열기, 패키지 설치, Earth Engine 인증 |
| 2. 영상 불러오기 | 15분 | Sentinel-2 발화 전(3/14)·발화 후(4/8), 구름·물 가리기 |
| 3. 지수 계산 | 20분 | NDVI·NBR·dNBR, 피해 등급 지도, 등급별 면적 |
| 4. AI 학습 | 30분 | dNBR로 정답 1/0, 기준선·MLP·U-Net, 검증 영역 채점, 피해 확률 지도 |
| 5. 검증·해석 | 20분 | FIRMS 화점 비교, 잔설: dNBR vs AI, 결과 해석 |

## 자료

- Copernicus Sentinel-2 L2A (ESA), Google Earth Engine `COPERNICUS/S2_SR_HARMONIZED`
- NASA FIRMS 화점 (Google Earth Engine `FIRMS`)
