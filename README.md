# 🎨 Connecting K-Color

**색으로 유물을 발견하는 데이터 기반 인터랙티브 웹 콘텐츠**

한국관광 데이터랩을 활용해 문화관광 맥락과 분석 대상을 선정하고,  
국립중앙박물관 소장품 이미지에서 대표색을 추출해  
**별자리형 인터랙션으로 유물을 탐색하는 웹서비스**를 구현했습니다.

🔗 사이트 바로가기: https://connecting-kcolor.vercel.app/

📁 Portfolio  
([Connecting K-Color Portfolio.pdf](https://github.com/user-attachments/files/32713936/Connecting.K-Color.Portfolio.pdf))

---

## 💡 프로젝트 목표

문화유산 정보는 충분하지만,  
처음 접하는 사용자에게는 **무엇을 먼저 봐야 하는지 발견하는 과정**이 어렵다고 생각했습니다.

Connecting K-Color는 긴 설명을 먼저 보여주는 대신

**색 발견 → 관계 탐색 → 직접 연결 → 유물 발견 → 정보 확인**

흐름으로 유물을 경험하도록 설계했습니다.

---

## 📊 데이터 활용

### 한국관광 데이터랩
프로젝트 주제와 분석 대상 선정을 위해 다음 데이터를 활용했습니다.

- 지역별 방문자 수
- 관광지 검색 순위
- 방문자 체류 특성
- 외국인 방문 현황

서울의 높은 방문 규모와 문화관광·역사관광 검색 노출을 확인한 뒤  
**국립중앙박물관을 분석 대상으로 선정**했습니다.

### 유물 이미지 데이터
국립중앙박물관 소장품 **8점**을 분석하고,  
각 유물에서 대표색 5개씩을 추출해 **총 40개의 색 데이터**를 구성했습니다.

---

## 🔎 핵심 분석

### 1. 대표색 추출
유물 이미지의 배경을 제외한 픽셀을 분석하고  
**MiniBatch K-means**를 활용해 유물별 대표색 5개를 추출했습니다.

### 2. CIELAB 변환
RGB 값을 CIELAB 색공간으로 변환해  
사람이 느끼는 색 차이에 가까운 방식으로 색상 관계를 비교했습니다.

### 3. 색상 특징 분석
- 대표색 사용 비율
- Color Entropy
- LAB 평균 색거리

를 활용해 유물별 색의 다양성과 특징을 비교했습니다.

### 4. 별자리형 시각화
40개의 색상 관계를 2차원 좌표로 변환해  
비슷한 색은 가깝게 배치하고, 같은 유물의 5색을 하나의 그룹으로 연결했습니다.

---

## ⚙️ 서비스 구조

색상 점 탐색  
→ 같은 유물의 5색 활성화  
→ 사용자가 직접 점 연결  
→ 별자리 완성  
→ 유물 공개  
→ 색상·유물 정보 탐색

---

## ✨ 주요 기능

- 40개 대표색 기반 별자리 인터페이스
- Hover 시 같은 유물의 5색 강조
- 드래그 방식의 별자리 연결
- 연결 완료 시 유물 공개
- 사용자가 만든 연결 형태 유지
- 색상명·HEX·설명 팝업
- 유물 이야기 아코디언
- 국립중앙박물관 공식 페이지·지도 연결
- 모바일 반응형 UI
- GA4 사용자 행동 이벤트 수집

---

## 📈 GA4 초기 테스트

Google Analytics 4를 연결해  
방문자 수보다 **사용자가 실제 기능을 어떻게 이용했는지**를 확인했습니다.

- 연결 시작 24회
- 연결 완료 23회
- **핵심 인터랙션 완성률 95.8%**
- 유물 공개 24회
- 색상 상세 탐색 29회
- 총 이벤트 318회

초기 표본 규모가 작아 일반화된 성과보다는  
**핵심 인터랙션이 실제 탐색 행동으로 이어지는지 확인한 테스트 결과**로 활용했습니다.

---

## 🛠 Tech Stack

**Data Analysis**  
Python · Pandas · NumPy · scikit-learn · Jupyter Notebook

**Color Analysis**  
CIELAB · MiniBatch K-means · MDS

**Frontend**  
HTML · CSS · JavaScript

**Analytics**  
Google Analytics 4

**Deployment**  
GitHub · Vercel

---

## 🎨 서비스 구현

분석 결과를 단순 그래프로 보여주는 대신  
**색상 관계 자체를 웹 인터페이스 구조로 활용**했습니다.

- 색상 좌표 → 별의 위치
- 유물별 대표색 → 5개 별 그룹
- 사용자의 연결 행동 → 유물 공개
- 색상 분석 결과 → 상세 팔레트와 정보 제공

즉, 데이터 분석 결과가  
**시각화 → 인터랙션 → 정보 탐색 경험**으로 이어지도록 구현했습니다.

---

## ⚠️ 한계

- 현재 분석 대상은 국립중앙박물관 소장품 8점
- 이미지 촬영 조건에 따라 색 추출 결과가 달라질 수 있음
- 초기 GA4 테스트의 사용자 표본이 적음
- 색각 다양성을 고려한 접근성 개선 필요

---

## 🚀 향후 확장

- 국립중앙박물관 소장품 데이터 확대
- 시대·주제별 컬렉션 구성
- 사용자가 선택한 색 기반 유사 유물 추천
- 다국어 콘텐츠 확장
- 공식 소장품 데이터 연동
- GA4 사용자 행동 기반 UX 개선

---

## 📎 Portfolio
프로젝트의 관광 데이터 분석, 색채 분석,  핵심 코드, UX 개선 및 GA4 결과는 포트폴리오 PPT에서 자세히 확인할 수 있습니다.

<img width="1280" height="720" alt="슬라이드1" src="https://github.com/user-attachments/assets/5e64ee49-ef67-4431-ba22-f92aa009450a" />
<img width="1280" height="720" alt="슬라이드2" src="https://github.com/user-attachments/assets/07b918fa-488d-4631-81ef-522ce9f56363" />
<img width="1280" height="720" alt="슬라이드3" src="https://github.com/user-attachments/assets/fa522968-c90b-4f3d-ac13-6b657de14346" />
<img width="1280" height="720" alt="슬라이드4" src="https://github.com/user-attachments/assets/efa6f376-1328-454c-a8bf-a205959bc90f" />
<img width="1280" height="720" alt="슬라이드5" src="https://github.com/user-attachments/assets/e9500fac-0770-41f2-ac19-67cd037ab899" />
<img width="1280" height="720" alt="슬라이드6" src="https://github.com/user-attachments/assets/34c32df9-c684-4363-90c3-1aa816a70369" />
<img width="1280" height="720" alt="슬라이드7" src="https://github.com/user-attachments/assets/5c54bc87-dce4-41b8-bd67-7a10f588e660" />
<img width="1280" height="720" alt="슬라이드8" src="https://github.com/user-attachments/assets/359159c6-a3e9-4de5-823b-670bcbac5d35" />
<img width="1280" height="720" alt="슬라이드9" src="https://github.com/user-attachments/assets/87be0f3a-c6da-4ea8-94fa-861a55e7095f" />
<img width="1280" height="720" alt="슬라이드10" src="https://github.com/user-attachments/assets/2b60dbae-c3fb-49d7-9e65-ea2a851d5992" />
<img width="1280" height="720" alt="슬라이드11" src="https://github.com/user-attachments/assets/76d358a1-9125-4a32-b871-f817ee84abed" />
<img width="1280" height="720" alt="슬라이드12" src="https://github.com/user-attachments/assets/bb8bba90-ef28-4d7a-a16d-19b4e03b85d2" />
<img width="1280" height="720" alt="슬라이드13" src="https://github.com/user-attachments/assets/3d239aa7-94e0-449f-ae48-af477b716a28" />
<img width="1280" height="720" alt="슬라이드14" src="https://github.com/user-attachments/assets/73f222cf-9b52-411c-8292-03e93e62241f" />
<img width="1280" height="720" alt="슬라이드15" src="https://github.com/user-attachments/assets/5a17fff4-44d3-4bcd-a936-b6a180cf1537" />
<img width="1280" height="720" alt="슬라이드16" src="https://github.com/user-attachments/assets/592b1a5f-2ac5-4012-b4ee-a1770c3ffe77" />
<img width="1280" height="720" alt="슬라이드17" src="https://github.com/user-attachments/assets/77f84187-3052-474d-80d0-2343fb120fd6" />
<img width="1280" height="720" alt="슬라이드18" src="https://github.com/user-attachments/assets/d627c3f3-cf96-42a5-97db-740d5bd0bf8c" />
<img width="1280" height="720" alt="슬라이드19" src="https://github.com/user-attachments/assets/1d8ce0c9-ae93-4b60-81a7-f304ae853c06" />
<img width="1280" height="720" alt="슬라이드20" src="https://github.com/user-attachments/assets/0321d99d-90e3-4cb5-8326-93fc4c3823b1" />
<img width="1280" height="720" alt="슬라이드21" src="https://github.com/user-attachments/assets/0e044e0b-5399-4166-8c47-e4e31eb76421" />
<img width="1280" height="720" alt="슬라이드22" src="https://github.com/user-attachments/assets/a8b1a6ab-7fe1-4fe8-9e3f-19e75a349738" />
<img width="1280" height="720" alt="슬라이드23" src="https://github.com/user-attachments/assets/dbd531ff-ee4f-48cc-915d-31f2245a5624" />
<img width="1280" height="720" alt="슬라이드24" src="https://github.com/user-attachments/assets/b13234fa-e624-4ab7-ab32-a2da70013c63" />
<img width="1280" height="720" alt="슬라이드25" src="https://github.com/user-attachments/assets/bdbb4caa-d0d7-4c09-8088-18207d5a6eef" />
<img width="1280" height="720" alt="슬라이드26" src="https://github.com/user-attachments/assets/6012a74a-e623-4cae-8053-7ce3a04971e4" />
<img width="1280" height="720" alt="슬라이드27" src="https://github.com/user-attachments/assets/798d21f6-dc76-4023-9b6a-bf7804af994c" />
<img width="1280" height="720" alt="슬라이드28" src="https://github.com/user-attachments/assets/1cf96162-c6d1-4a5c-94fb-fa2ba3277650" />
<img width="1280" height="720" alt="슬라이드29" src="https://github.com/user-attachments/assets/bae7161d-737c-4179-a1f7-713437c62087" />
<img width="1280" height="720" alt="슬라이드30" src="https://github.com/user-attachments/assets/1d6ab256-7744-4212-a4eb-a93a7189b97b" />
<img width="1280" height="720" alt="슬라이드31" src="https://github.com/user-attachments/assets/da82fe5a-dce4-4698-a968-e0b9b44deeb4" />
<img width="1280" height="720" alt="슬라이드32" src="https://github.com/user-attachments/assets/a01dc71a-0b15-4a32-b64b-25999abcf024" />


