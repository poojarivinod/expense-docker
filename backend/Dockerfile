#FROM node:20
# we can take node 20. alpine version to reduce image size # docker hub --> explore --> search as 20.18 
FROM node:20.18.3-alpine3.21 
WORKDIR /opt/backend
# here . dot means current directory, copy the package.json and *.js to /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
# we can use this when we have bridge network
ENV DB_HOST="mysql"
# we can use this when we have host network
#ENV DB_HOST="localhost"
CMD ["node", "index.js"]