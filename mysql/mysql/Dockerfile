FROM mysql:latest

# Japanese
RUN apt-get update \
    && apt-get install -y locales \
    && locale-gen ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8
RUN localedef -f UTF-8 -i ja_JP ja_JP.utf8

EXPOSE 3306

COPY ./my.cnf /etc/mysql/conf.d/my.cnf

#docker runに実行される
CMD ["mysqld"]