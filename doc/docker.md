# Docker

## Dockerfile
- Selecciona una imagen base
FROM alpine:latest

- Define el directorio de trabajo
WORKDIR /app

- Copia archivos locales al contenedor
COPY . .

- Ejecuta un comando al construir la imagen
RUN apk add --no-cache python3

- Especifica el comando predeterminado al iniciar el contenedor
CMD ["python3", "app.py"]

## Docker Compose
```
version: '3'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
```

## Red personalizada y variables de entorno
```
version: '3'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
```

## Persistencia de datos con volumenes
```
version: '3'

services:
  db:
    image: postgres:latest
    volumes:
      - pg_data:/var/lib/postgresql/data

volumes:
  pg_data:
```
## Docker en un pipeline CI/CD
```
stages:
  - build
  - test
  - deploy

services:
  - docker:dind

variables:
  DOCKER_DRIVER: overlay2

before_script:
  - docker info

build:
  stage: build
  script:
    - docker build -t miapp:latest .

test:
  stage: test
  script:
    - docker run miapp:latest python test.py

deploy:
  stage: deploy
  only:
    - master
  script:
    - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
    - docker push miapp:latest

```