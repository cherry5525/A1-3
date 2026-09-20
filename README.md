# 🥗 MealGenie - AI 맞춤 식단 추천 서비스

성별, 나이, 목적에 맞는 개인 맞춤 식단을 AI가 추천해주는 웹 서비스입니다!

🔗 **배포 URL**: https://a1-3-tau.vercel.app/
📦 **GitHub**: https://github.com/cherry5525/A1-3

---

## 📖 서비스 소개

MealGenie는 매번 "오늘 뭐 먹지?"를 고민하는 사용자를 위한 AI 식단 추천 서비스입니다.
성별·나이·기간·목적·선호 음식·알레르기·키·몸무게 등 개인별 특성을 입력하면,
OpenAI GPT가 사용자에게 딱 맞는 맞춤 식단을 추천해줍니다.

### 주요 특징
- 🤖 **AI 맞춤 추천**: 8개 입력값을 기반으로 개인화된 식단 제공
- 📊 **BMI 자동 계산**: 키·몸무게 입력 시 BMI를 계산해 식단에 반영
- 🚫 **알레르기 반영**: 입력한 알레르기 재료는 식단에서 자동 제외
- 🌙 **다크 모드**: 사용자 선호에 맞는 테마 전환
- 📋 **결과 복사 / 📕 PDF 저장**: 추천 결과를 손쉽게 저장·활용
- 💾 **입력값 자동 저장**: 재방문 시 이전 입력값 복원

---

## 🛠 기술 스택

| 구분 | 기술 |
|------|------|
| Frontend | HTML, CSS, JavaScript (Vanilla) |
| Backend | Python (Flask) - Vercel Serverless Functions |
| AI API | OpenAI GPT (gpt-5-mini) |
| 배포 | Vercel |
| 외부 라이브러리 | html2canvas, jsPDF (PDF 저장 기능) |

---

## 📂 프로젝트 구조

A1-3/
├── api/
│ └── recommend.py # AI 식단 추천 엔드포인트
├── css/
│ └── style.css # 스타일 (반응형/다크모드 포함)
├── .env # 환경 변수 (API 키) - Git 미포함
├── .gitignore
├── requirements.txt # Python 패키지 목록
├── index.html # 메인 페이지 (소개/추천/FAQ)
├── README.md
├── 서비스 기획서.md
└── vercel.json # Vercel 배포 설정


---

## 🚀 실행 방법 (로컬)

### 1. 저장소 클론
```bash
git clone https://github.com/cherry5525/A1-3.git

```

### 2. 패키지 설치
```bash
pip install -r requirements.txt

```

### 3. 환경 변수 설정
```
OPENAI_API_KEY=발급받은_API_키

```

### 4. 로컬 실행
```bash
python api/recommend.py

```
---


## ☁️ 배포 방법 (Vercel)
GitHub 저장소를 Vercel에 연동합니다.
Vercel 프로젝트의 Settings → Environment Variables에서 환경 변수를 등록합니다.
OPENAI_API_KEY : 발급받은 API 키 (codyssey API사용)
main 브랜치에 push하면 자동으로 배포됩니다.
배포 완료 후 발급된 URL에서 동작을 확인합니다.

## 🔑 환경 변수
변수명	설명
OPENAI_API_KEY	OpenAI API 인증 키 (codyssey API사용)
⚠️ API 키는 절대 코드에 직접 입력하지 않으며, .env 파일(로컬) 및 Vercel 환경 변수(배포)로만 관리합니다.
.env 파일은 .gitignore에 등록되어 GitHub에 업로드되지 않습니다.

## 🧪 AI 기능 동작 예시
상황	입력	결과
정상 입력	여성 / 25 / 7 / 다이어트 / 샐러드	맞춤 식단 표시
빈 입력	나이·기간 미입력	"⚠️ 나이와 기간을 입력해주세요!" 안내
서버 오류	API 응답 실패	"😢 추천을 받지 못했어요. 잠시 후 다시 시도해주세요." 안내

---



## 🎯 과제 목표

1. HTML / CSS / JavaScript의 역할
웹 페이지는 사람의 몸에 비유할 수 있다.

언어	역할	비유
HTML	구조/내용 (뼈대)	뼈, 골격
CSS	디자인/스타일 (외형)	피부, 옷
JavaScript	동작/기능 (움직임)	근육, 신경
HTML (HyperText Markup Language)
웹 페이지의 내용과 구조를 정의한다.
```
<!-- 제목과 버튼의 구조를 정의 -->
<h1>안녕하세요</h1>
<button id="myBtn">클릭하세요</button>

CSS (Cascading Style Sheets)
HTML 요소의 디자인과 스타일을 담당한다.
```
/* 버튼을 파란색, 둥근 모양으로 스타일링 */
button {
  background-color: blue;
  border-radius: 10px;
  color: white;
}

JavaScript
사용자와의 **상호작용(동작)**을 구현한다.
```
// 버튼 클릭 시 경고창 표시
document.getElementById("myBtn").addEventListener("click", () => {
  alert("버튼이 눌렸습니다.");
});