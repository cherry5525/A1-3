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

```
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
```

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
| 상황	| 입력	| 결과 |
|-----|-----|--------|
| 정상 입력	| 여성 / 25 / 7 / 다이어트 / 샐러드	| 맞춤 식단 표시 |
| 빈 입력	| 나이·기간 미입력	| "⚠️ 나이와 기간을 입력해주세요!" 안내 |
| 서버 오류	| API 응답 실패	| "😢 추천을 받지 못했어요. 잠시 후 다시 시도해주세요." 안내 |

---



## 🎯 과제 목표

### 1. HTML / CSS / JavaScript의 역할

웹 페이지는 사람의 몸에 비유할 수 있다.

| 언어	| 역할	| 비유 |
|-----|-----|--------|
|HTML	| 구조/내용 (뼈대)	| 뼈, 골격 |
|CSS	| 디자인/스타일 (외형)	| 피부, 옷 |
|JavaScript	| 동작/기능 (움직임)	| 근육, 신경 |

HTML (HyperText Markup Language)
웹 페이지의 내용과 구조를 정의한다.
```
<!-- 제목과 버튼의 구조를 정의 -->
<h1>안녕하세요</h1>
<button id="myBtn">클릭하세요</button>
```

CSS (Cascading Style Sheets)
HTML 요소의 디자인과 스타일을 담당한다.
```
/* 버튼을 파란색, 둥근 모양으로 스타일링 */
button {
  background-color: blue;
  border-radius: 10px;
  color: white;
}
```

JavaScript
사용자와의 **상호작용(동작)**을 구현한다.
```
// 버튼 클릭 시 경고창 표시
document.getElementById("myBtn").addEventListener("click", () => {
  alert("버튼이 눌렸습니다.");
});
```
### 2. 사용자 입력 → fetch 요청 → 화면 반영 흐름
데이터는 다음과 같은 순서로 처리된다.

```
[사용자 입력] → [JavaScript 감지] → [fetch로 서버 요청]
     → [서버 응답] → [JavaScript가 화면 업데이트]
```

예시 코드
```javascript
// 1. 사용자가 입력한 값 가져오기
const input = document.getElementById("userInput").value;

// 2. fetch로 서버에 요청 (비동기 통신)
fetch("/api/chat", {
  method: "POST",                          // 데이터 전송 시 POST 사용
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ message: input }) // 입력값을 JSON으로 변환해 전송
})
  .then(response => response.json())         // 3. 응답을 JSON으로 변환
  .then(data => {
    // 4. 받은 데이터를 화면에 반영
    document.getElementById("result").innerText = data.answer;
  });
```
핵심 용어

fetch: 자바스크립트가 서버에 데이터를 요청하는 함수
비동기(async): 응답을 기다리는 동안 화면이 멈추지 않는 방식

### 3. Vercel Serverless Functions
**Serverless(서버리스)**는 서버가 없다는 뜻이 아니라, 개발자가 서버를 직접 관리하지 않아도 되는 방식을 의미한다. 함수는 필요할 때만 실행되고 종료되면 사라진다.

구조 (프론트엔드 → 백엔드 호출)
```
[프론트엔드 JS]  →  fetch("/api/함수이름")  →  [Vercel Serverless Function (Python)]
                                                    ↓
                                            [외부 API 호출 등 처리]
                                                    ↓
[화면에 결과 표시] ← 응답 ← ← ← ← ← ← ← ← ← ← ← ←
```
Python 예시 (/api/hello.py)
```python
# Vercel은 이 파일을 자동으로 API로 변환한다
from http.server import BaseHTTPRequestHandler
import json

class handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'application/json')
        self.end_headers()
        # 프론트로 보낼 응답
        self.wfile.write(json.dumps({"answer": "안녕하세요!"}).encode())
```
별도 서버 없이 백엔드 로직(예: OpenAI API 호출)을 안전하게 처리할 수 있다.

### 4. 환경 변수로 API 키를 관리하는 이유
**환경 변수(Environment Variable)**는 코드에 직접 작성하지 않고 외부에 별도로 보관하는 비밀 설정값이다.

잘못된 예시 (위험)
```javascript
const apiKey = "sk-1234실제키노출"; // GitHub에 올리면 해킹 위험
```

올바른 예시 (안전)
```python
import os
api_key = os.environ.get("OPENAI_API_KEY")  # 외부에서 안전하게 불러옴
```

환경 변수를 사용하는 이유

보안: 코드에 키가 노출되면 누구나 도용할 수 있다.
비용 방지: 유료 API 키가 유출되면 예상치 못한 요금이 발생한다.
관리 편의: 환경(로컬/배포)마다 다른 값을 쉽게 설정할 수 있다.

### 5. 로컬 환경 vs 배포 환경
| 구분	| 로컬 환경	| 배포 환경 |
|-----|-----|--------|
| 위치	| 내 컴퓨터	| 인터넷 서버(Vercel) |
| 주소	| localhost:3000	| https://내앱.vercel.app |
| 용도	| 개발/테스트	| 실제 사용자 접속 |

문제 수정 및 재배포 흐름
```
1. 배포된 앱에서 오류 발견
2. 로컬에서 코드 수정 및 테스트
3. git commit → git push (GitHub에 업로드)
4. Vercel이 자동으로 감지하여 재배포
5. 배포 완료 후 재확인
```
자주 발생하는 문제: 로컬에서는 정상 동작하지만 배포 후 오류가 발생하는 경우가 많다. 대부분 환경 변수 설정 누락이 원인이며, 배포 환경에도 API 키를 별도로 등록해야 한다.

### 6. AI 코딩 도구를 이해하며 사용하기
AI가 코드를 생성하더라도 그 원리를 설명할 수 있어야 실제 문제 해결이 가능하다.

예시 상황
```javascript
// AI가 생성한 코드
fetch("/api/data")
  .then(res => res.json())
  .then(data => console.log(data.name));
```
오류 발생 시 점검 사항

data가 비어 있어 undefined가 반환되는지 확인
API 주소가 올바른지 확인
브라우저 네트워크 탭에서 실제 응답 확인
AI는 잘못된 코드도 생성할 수 있으므로, 오류의 원인을 스스로 설명할 수 있는 능력이 중요하다.

전체 흐름 요약
여섯 가지 개념은 하나의 흐름으로 연결된다.
```
HTML/CSS/JS로 화면 구성
   → JS가 fetch로 서버(Serverless) 호출
      → 환경 변수로 API 키 안전하게 사용
         → 로컬에서 개발 후 배포
            → 문제 발생 시 원인 파악 후 재배포
```