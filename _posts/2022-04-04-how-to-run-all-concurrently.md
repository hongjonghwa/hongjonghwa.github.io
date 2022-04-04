---
title: "클라이언트 & 백엔드 동시에 실행"
categories:
  - programming
tags:
  - javascript
  - npm-run-all
toc: false
---


## package.json
``` json
{
  "name": "test",
  "version": "0.0.0",
  "description": "npm version.",
  "scripts": {
    "develop:backend": "backend/gradlew -p backend bootRun",
    "develop:frontend": "wait-on http://localhost:8000/ && npm --prefix frontend run develop",
    "develop": "cross-env FORCE_COLOR=1 npm-run-all -l -p develop:*"
  },
  "author": "JH",
  "dependencies": {
    "cross-env": "^7.0.3",
    "npm-run-all": "^4.1.5",
    "wait-on": "^6.0.1"
  }
}
```


