# 사용할 베이스 이미지 선택
FROM node:latest as build

# 작업 디렉토리 설정
WORKDIR /app

# 앱 종속성 설치
COPY package*.json ./
RUN npm install

# 앱 소스 추가
COPY . .

# 앱 빌드
RUN npm run build

# Production stage
FROM nginx:latest

# Nginx 설정 파일을 복사하여 기본 설정을 변경
COPY --from=build /app/build /usr/share/nginx/html

# 80 포트 노출
EXPOSE 8080

# Nginx 실행
CMD ["nginx", "-g", "daemon off;"]
