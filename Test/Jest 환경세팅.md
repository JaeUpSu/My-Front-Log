<img src="../Image/testcodeLogo.jpeg" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Jest 환경세팅을 알아보자 (at React)`

<br>


* **설치**
* **babel.config.js**
* **jest.config.ts**
* **setupJest.js**
* **package.json**

<br>

> 설치

<br>

&nbsp;&nbsp;&nbsp;CRA 에서 Typescript 와 MSW 를 사용할 때

```
npm i jest jsdom

npm i --save-dev @babel/cli @babel/core @babel/preset-env @babel/preset-typescript @types/jest @jest/globals jest-environment-jsdom jest-fetch-mock babel-jest ts-jest msw 
```

<br>

> babel.config.js

<br>

```
module.exports = {
  presets: [
    ["@babel/preset-env", { targets: { node: "current" } }],
    "@babel/preset-react",
    "@babel/preset-typescript",
  ],
};
```
<br>
<br>

> jest.config.ts

<br>

```
export default {
  preset: "ts-jest",
  testEnvironment: "jsdom",
  setupFilesAfterEnv: ["<rootDir>/setupJest.js"],
  testMatch: ["**/__tests__/**/*.ts?(x)", "**/?(*.)+(spec|test).(ts|tsx)"],
  transform: {
    "^.+\\.(ts|tsx)$": "ts-jest",
    "^.+\\.(js|jsx)$": "babel-jest",
  },
  moduleFileExtensions: ["ts", "tsx", "js", "json", "node"],
  transformIgnorePatterns: ["<rootDir>/node_modules/"],
  moduleNameMapper: {
    "\\.(css|less|scss|sass)$": "identity-obj-proxy",
  },
};
```
<br>
<br>

> setupJest.js

<br>

```
// ts 테스트
import "@testing-library/jest-dom";
// tsx 테스트
import "@testing-library/jest-dom/extend-expect";
```
<br>
<br>

> package.json

<br>

```
{
  "name": "cmgg_project",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "jest": "^29.5.0",
    "jsdom": "^21.1.1",
    "ts-node": "^10.9.1",
    "typescript": "^4.9.5",
    "web-vitals": "^2.1.4"
  },
  "devDependencies": {
    "@babel/cli": "^7.21.0",
    "@babel/core": "^7.21.4",
    "@babel/preset-env": "^7.21.4",
    "@babel/preset-typescript": "^7.21.4",
    "@types/jest": "^29.5.0",
    "@jest/globals": "^29.5.0",
    "jest-environment-jsdom": "^29.5.0",
    "jest-fetch-mock": "^3.0.3",
    "babel-jest": "^29.5.0",
    "ts-jest": "^29.1.0",
    "msw": "^1.2.1"
  },
  "msw": {
    "workerDirectory": "public"
  }
}
```