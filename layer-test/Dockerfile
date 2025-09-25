#FROM node:20
# we can take node 20. alpine version to reduce image size # docker hub --> explore --> search as 20.18 
FROM node:20.18.3-alpine3.21 
# add user and group in alpine--> stack overflow
# we are using alpine operaing system, so we need add user in following manner
# group name is expense(-S), user name is expense(-S), we are adding expense(-G)
RUN addgroup -S expense && adduser -S expense -G expense
# we are creating /opt/backend repository
RUN mkdir /opt/backend
# handover the /opt/backend repository permission to expense
RUN chown -R expense:expense /opt/backend
WORKDIR /opt/backend
# here . dot means current directory, copy the package.json and *.js to /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
# we can use this when we have bridge network
#ENV DB_HOST="mysql" # this change is made to test image layer
# we can use this when we have host network
#ENV DB_HOST="localhost"
USER expense
CMD ["node", "index.js"]