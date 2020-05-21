FROM mysql@sha256:bf17a7109057494c45fba5aab7fc805ca00ac1eef638dfdd42b38d5a7190c9bb

#linux env variable
ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_DATABASE=northwind 

#copy the files into /docker-entrypoint-initdb.d directory
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# add healthcheck -v2
HEALTHCHECK --interval=60s --timeout=30s --start-period=15s --retries=3 \
CMD  mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD}|| exit 1
#mysqladmin ping -uroot -pchangeit

#EXPOSE 3306

# where MySQL stores the database -v3
VOLUME /var/lib/mysql

