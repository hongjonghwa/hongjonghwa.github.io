---
title: "Keycloak 설정"
categories:
  - 아키텍트
tags:
  - IAM, Auth, Identify Provider
---

## Test

### docker
``` sh
docker run --rm --name keycloak_test -p 8101:8080 \
    -e KEYCLOAK_ADMIN=admin \
    -e KEYCLOAK_ADMIN_PASSWORD=<admin_password> \
    -e KC_DB=mysql \
    -e KC_FEATURES=token-exchange \
    -e KC_DB_URL='jdbc:mysql://<db_host>/<db_database>?characterEncoding=UTF-8&useSSL=false' \
    -e KC_DB_USERNAME=<db_user> \
    -e KC_DB_PASSWORD=<db_password> \
    quay.io/keycloak/keycloak:17.0.1 \
    start-dev
```

## Prod

### docker
``` sh
docker run -d --name keycloak_prod -p 8001:8080 \
    -e KEYCLOAK_ADMIN=admin \
    -e KEYCLOAK_ADMIN_PASSWORD=<admin_password> \
    -e KC_DB=mysql \
    -e KC_FEATURES=token-exchange \
    -e KC_DB_URL='jdbc:mysql://<db_host>/<db_database>?characterEncoding=UTF-8&useSSL=false' \
    -e KC_DB_USERNAME=<db_user> \
    -e KC_DB_PASSWORD=<db_password> \
    quay.io/keycloak/keycloak:17.0.1 \
    start --proxy edge --hostname <hostname> --auto-build
```

### nginx
``` nginx
    server {
        listen  80;
        listen  443 ssl http2;
        server_name ${hostname};
        location / {
            proxy_pass http://127.0.0.1:8001;
            proxy_set_header Host $http_host;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
        ssl_certificate     /etc/ssl/${cert-file};
        ssl_certificate_key /etc/ssl/${private key-file};
    }
```

