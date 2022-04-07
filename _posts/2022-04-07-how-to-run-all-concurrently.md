---
title: "클라이언트 & 백엔드 서버 동시에 실행"
categories:
  - programming
tags:
  - javascript
  - npm-run-all
toc: false
---


## Spring 백엔드 + JS 프로트엔드(npm)
#### **`package.json`**
``` json
{
  "version": "0.0.0",
  "scripts": {
    "develop:backend": "backend/gradlew -p backend bootRun",
    "develop:frontend": "wait-on http://localhost:8000/ && npm --prefix frontend run develop",
    "develop": "cross-env FORCE_COLOR=1 npm-run-all -l -p develop:*"
  },
  "dependencies": {
    "cross-env": "^7.0.3",
    "npm-run-all": "^4.1.5",
    "wait-on": "^6.0.1"
  }
}
```
  
  
  

## JS 백엔드 + JS 프로트엔드 (yarn)
#### **`package.json`**
``` json
{
  "version": "0.0.0",
  "scripts": {
    "develop:backend": "yarn --cwd backend start:dev",
    "develop:frontend": "wait-on http://localhost:3001/ && yarn --cwd frontend dev",
    "develop": "cross-env FORCE_COLOR=1 npm-run-all -l -p develop:*"
  },
  "dependencies": {
    "cross-env": "^7.0.3",
    "npm-run-all": "^4.1.5",
    "wait-on": "^6.0.1"
  }
}
```
