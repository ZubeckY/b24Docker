FROM mysql:5.6

RUN apt-get update && apt-get install -y \
    mc

#добавление директив mysqld
COPY bx.cnf /etc/mysql/mysql.conf.d/