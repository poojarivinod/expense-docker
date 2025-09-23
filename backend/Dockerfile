FROM node:20
WORKDIR /opt/backend
# here . dot means current directory, copy the package.json and *.js to /opt/backend
COPY package.json .
COPY *.js .
RUN npm install
ENV DB_HOST="mysql"
CMD ["node", "index.js"]