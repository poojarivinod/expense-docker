#docker hub --> mysql(official)
FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1
# it will copy backend.sql to /docker-entrypoint-initdb.d #search in docker hub --> mysql(official) about /docker-entrypoint-initdb.d
COPY scripts/*.sql  /docker-entrypoint-initdb.d


