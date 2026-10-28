# 이상형 매칭

학급 축제 부스용 이상형 매칭 시스템이에요. 참가자 화면, 사회자 화면, 전광판 화면이 실시간으로 연결돼요.
GitHub Pages로 사이트를 올리고, 실시간 데이터는 Firebase(무료)에 저장해요.

## 1. Firebase 준비 (약 5분)

1. https://console.firebase.google.com 에서 **프로젝트 추가** (Google 애널리틱스는 꺼도 돼요).
2. 왼쪽 메뉴 **빌드 > Firestore Database > 데이터베이스 만들기**
   - 위치: `asia-northeast3 (서울)`
   - **프로덕션 모드**로 시작
3. Firestore의 **규칙** 탭에 이 저장소의 `firestore.rules` 내용을 그대로 붙여 넣고 **게시**.
4. **프로젝트 설정(톱니바퀴) > 일반 > 내 앱 > 웹(</>)** 으로 앱 등록 → 나오는 `firebaseConfig` 값을
   `firebase-config.js`에 붙여 넣기.

## 2. GitHub Pages로 배포

1. GitHub에서 새 저장소 만들기 (Public).
2. 이 폴더의 파일을 전부 올리기: `index.html`, `firebase-config.js`, `firestore.rules`, `README.md`, `.nojekyll`
3. 저장소 **Settings > Pages > Build and deployment**
   - Source: **Deploy from a branch**
   - Branch: **main** / **/(root)** → Save
4. 1~2분 뒤 `https://<아이디>.github.io/<저장소이름>/` 로 접속.

## 3. 행사 당일

- 모든 크롬북에서 위 주소를 열고 실행 키를 입력해요.
- 홈에서 기기마다 **참가자 / 사회자 / 전광판**을 골라요.
- 시작 전에 사회자 화면에서 **전체 초기화**를 두 번 눌러 연습 데이터를 지워요.

## 알아둘 점

- 실행 키는 화면 잠금용이에요. 코드를 보면 키가 보이니 진짜 보안 장치는 아니에요.
  키를 바꾸려면 `index.html`에서 `const KEY="jangjinone";`을 고치면 돼요.
- 사이트 주소를 아는 사람은 데이터를 보고 바꿀 수 있어요. 학생 이름과 학번이 저장되니,
  **행사가 끝나면 전체 초기화를 하고** Firestore 규칙의 `if true`를 `if false`로 바꿔 잠가 주세요.
- Firebase 무료 요금제(Spark)로 충분해요. 결제 정보는 넣지 않아도 돼요.

made by jangjinone · powered by GitHub
