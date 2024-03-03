# 1.개발환경 설정

## 1.1 ~ 1.2 리액트 환경설정
### 1.1.1 생성
* npx create-react-app +  (프로젝트 이름)
   프로젝트 이름 대문자 금지
 * npm start (프로젝트 폴더에서)

### 1.1.2 플러그인
*  Simple React Snippets
* Tailwind CSS IntelliSense

### 1.1.3  tailwindcss
* npm install -D tailwindcss
* npx tailwindcss init

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


## 1.3 MariaDB
* install 시 UTF-8  설정

```oracle
create database malldb

create user 'malldbuser'@'localhost' identified by  '1234';
create user 'malldbuser'@'%' identified by  '1234';

grant all privileges on malldb.* to 'malldbuser'@'localhost';
grant all privileges on malldb.* to 'malldbuser'@'%';
```

## 1.4 스프링 부트 설정
### 1.4.1 jdk 설치 
Open Jdk
* Amazon Corretto

### 1.4.2 STS   plugin
* Spring Boot Extension Pack

### 1.4.3  프로젝트 생성
* artifactid : 소문자

```
* Spring Boot DevTools
* Lombok
* Spring Web
* Spring Data Jpa
* MariaDB Driver
```

```properties
//main/resources/application.properties

spring.datasource.driver-classname=org.mariadb.jdbc.Driver
spring.datasource.url=jdbc:mariadb://localhost:3306/malldb
spring.datasource.username=malldbuser
spring.datasource.password=1234

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.show-sql=true
```
