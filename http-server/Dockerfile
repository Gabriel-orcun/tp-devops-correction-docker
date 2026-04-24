# Build stage for frontend
FROM node:12.16.3-stretch-slim AS frontend-build

WORKDIR /opt/front

COPY ../devops-front-main/ .

RUN npm install
RUN npm run build

# Apache stage
FROM httpd:2.4

COPY my-httpd.conf /usr/local/apache2/conf/httpd.conf
COPY --from=frontend-build /opt/front/dist /usr/local/apache2/htdocs/
