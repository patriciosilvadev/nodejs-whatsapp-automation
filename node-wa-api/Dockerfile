FROM node


ENV DATABASE_HOST mariaDB
ENV DATABASE_USER root
ENV DATABASE_PASSWORD dutamedia_dev
ENV DATABASE_NAME db_otpwhatsapp
ENV SERVER_URL localhost
ENV SERVER_PORT 8000


WORKDIR /app


RUN  apt update \
     && apt install -y wget netcat gnupg ca-certificates python3 make autoconf gcc g++ \
     && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
     && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
     && apt update \
     && apt install -y google-chrome-stable \
     && rm -rf /var/lib/apt/lists/*


COPY source/ .
RUN npm install


COPY entrypoint.sh .
RUN chmod +x ./entrypoint.sh
ENTRYPOINT ["./entrypoint.sh"]


EXPOSE 8000
CMD ["npm", "run", "start"]
