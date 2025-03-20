FROM alpine AS helper-clone
RUN apk add git 
WORKDIR /src 
ARG BRANCH_NAME=develop
RUN git clone https://github.com/mariano-italiano/lx-d_Mar.git && cd lx-d_Mar && git checkout $BRANCH_NAME 

FROM nginx:1.19.2 
LABEL "Application"="test docker app" 
MAINTAINER Marcin K

RUN apt-get update && apt-get install -y vim && apt-get clean && rm -rf /var/lib/apt/lists/* 
COPY --from=helper-clone /src/lx-d_Mar/index.html /usr/share/nginx/html/index.html
