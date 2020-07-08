# docker build -t sa-frontend .
# docker run -d -p 80:80 sa-frontend

FROM node:12 as build
COPY ./ ./
RUN npm install


FROM nginx
COPY --from=build build /usr/share/nginx/html
