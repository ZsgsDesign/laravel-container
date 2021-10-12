FROM zsgsdesign/laravel-php:latest

COPY ./oracle-sdk /tmp/oracle-sdk

RUN apk add --no-cache libaio-dev libnsl libc6-compat && \
unzip /tmp/oracle-sdk/instantclient-basic-linux.x64-12.2.0.1.0.zip -d /usr/local/ && \
unzip /tmp/oracle-sdk/instantclient-sdk-linux.x64-12.2.0.1.0.zip -d /usr/local/ && \
unzip /tmp/oracle-sdk/instantclient-sqlplus-linux.x64-12.2.0.1.0.zip -d /usr/local/ && \
ln -s /usr/local/instantclient_12_2 /usr/local/instantclient && \
ln -s /usr/local/instantclient/libclntsh.so.* /usr/local/instantclient/libclntsh.so && \
ln -s /usr/local/libclntshcore.so.* /usr/local/instantclient/libclntshcore.so && \
ln -s /usr/local/instantclient/libocci.so.* /usr/local/instantclient/libocci.so && \
ln -s /usr/local/instantclient/sqlplus /usr/bin/sqlplus && \
ln -s /usr/lib/libnsl.so.2 /usr/lib/libnsl.so.1 && \
ln -s /lib/libc.so.6 /usr/lib/libresolv.so.2 && \
ln -s /lib64/ld-linux-x86-64.so.2 /usr/lib/ld-linux-x86-64.so.2 && \
docker-php-ext-configure oci8 --with-oci8=instantclient,/usr/local/instantclient && \
docker-php-ext-install oci8 && \
rm -rf /tmp/oracle-sdk