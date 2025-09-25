# builder environment , builder(we can give any name) is just a name to indicate
FROM node:20.18.3-alpine3.21 AS builder
WORKDIR /opt/backend
# here . dot means current directory, copy the package.json and *.js to /opt/backend
COPY package.json ./
# / is used when we have more than one file, otherwise won't develops layer image
COPY *.js ./
RUN npm install



# runner environment
#FROM node:20
# we can take node 20. alpine version to reduce image size # docker hub --> explore --> search as 20.18 
# IC-1
FROM node:20.18.3-alpine3.21 
# add user and group in alpine--> stack overflow
# we are using alpine operaing system, so we need add user in following manner
# group name is expense(-S), user name is expense(-S), we are adding expense(-G)
#  on top of IC-1, instruction-2 is executed, save this as layer 2 image. IC-1 is removed
# && \ is to make all the RUN command under one layer image,otherwise craetes seperate layer image for each RUN command, this will reduces the build run time. 
RUN addgroup -S expense && adduser -S expense -G expense && \
# we are creating /opt/backend repository
# creates IC-2, on top of IC-2, instruction-3 is executed, save this as layer 3 image. IC-2 is removed
# && \ is to make all the RUN command under one layer image,otherwise craetes seperate layer image for each RUN command, this will reduces the build run time. 
    mkdir /opt/backend && \
# handover the /opt/backend repository permission to expense
# && \ is to make all the RUN command under one layer image,otherwise craetes seperate layer image for each RUN command, this will reduces the build run time.
    chown -R expense:expense /opt/backend
# we can use this when we have bridge network
# mysql is the container name, we don't need give the ip address or domain name as we given previously in the terraorm
ENV DB_HOST="mysql"
# we can use this when we have host network
#ENV DB_HOST="localhost"
WORKDIR /opt/backend
USER expense
# copy the output from builder environment /opt/backend into runner environment /opt/backend
COPY --from=builder /opt/backend /opt/backend
CMD ["node", "index.js"]