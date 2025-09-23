FROM node:20
WORKDIR /opt/backend
# here . dot means current directory, copy the package.json and *.js to /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
# we can use this when we have bridge network
#ENV DB_HOST="mysql"
# we can use this when we have host network
ENV DB_HOST="localhost"
CMD ["node", "index.js"]