# 1.개발환경 설정

## 1.1 ~ 1.2 리액트 환경설정
### 1.1.1 생성
* npx create-react-app +  (프로젝트 이름)
   프로젝트 이름 대문자 금지
* npm start (프로젝트 폴더에서)

### 1.1.2 플러그인
* Simple React Snippets
* Tailwind CSS IntelliSense

### 1.1.3  tailwindcss
```
npm install -D tailwindcss
npx tailwindcss init
npm install axios
npm install @reduxjs/toolkit react-redux
npm install react-cookie
npm i @tanstack/react-query
npm i @tanstack/react-query-devtools
npm install recoil
```

```javascript
//tailwind.css 
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
```css
/*src/index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```
### 1.1.4 index.js
2번 실행 방지
```javascript
// <StrictMode> 제거
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <App />
);
```
