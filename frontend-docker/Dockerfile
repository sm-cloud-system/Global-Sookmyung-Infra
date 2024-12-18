FROM node:18.20.5-alpine3.20 as builder
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN yarn
COPY . .
RUN yarn build

# nginx를 베이스 이미지로 사용
FROM nginx:1.14

# 타임존 설정
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 리액트 빌드 파일을 nginx/html로 복사
COPY --from=builder /app/build /usr/share/nginx/html

# default conf 파일 제거
RUN rm /etc/nginx/conf.d/default.conf

# 내가 작성한 conf 파일을 nginx로 복사
COPY ./nginx.conf /etc/nginx/conf.d

# 80번 포트를 노출
EXPOSE 80

# nginx 백그라운드 실행
CMD ["nginx", "-g", "daemon off;"]
