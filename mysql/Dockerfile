FROM mysql:5.6

# Japanese localization
RUN apt-get update \
    && apt-get install -y locales \
    && locale-gen ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8

RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8

EXPOSE 3306

RUN { \
    echo '[mysqld]'; \
    echo 'character-set-server=utf8mb4'; \
    echo 'collation-server=utf8mb4_general_ci'; \
    echo '[client]'; \
    echo 'default-character-set=utf8mb4'; \
} > /etc/mysql/conf.d/charset.cnf

#docker runに実行される
CMD ["mysqld", "--character-set-server=utf8mb4", "--collation-server=utf8mb4_unicode_ci"]