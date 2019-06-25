#docker build
FROM node:latest

#environment variables
ENV APP_PORT=3000 APP_DIR=/server \
    DB_HOST=nwdb DB_PORT=3306 \
    DB_USER=root DB_PASSWORD=changeit

#cd into directory
WORKDIR ${APP_DIR}

#copy files
ADD main.js .
ADD package.json .
#copy dir
ADD public public
ADD views views
ADD config config

#install libraries from package.json
RUN npm install

#docker run
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

ENTRYPOINT [ "node", "main.js" ]
