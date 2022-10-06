FROM node:alpine

ENV TZ "Asia/Shanghai"

RUN npm config set registry https://registry.npmmirror.com
RUN npm install -g socketlog-server


EXPOSE 1229 1116

CMD ["socketlog-server"]