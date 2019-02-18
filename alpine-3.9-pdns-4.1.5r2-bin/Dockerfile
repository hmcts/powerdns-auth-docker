FROM alpine:3.9

LABEL \
  MAINTAINER="Christoph Wiechert <wio@psitrax.de>" \
  CONTRIBUTORS="Mathias Kaufmann <me@stei.gr>, Cloudesire <dev@cloudesire.com>"

ENV REFRESHED_AT="2019-02-18" \
    AUTOCONF=mysql \
    MYSQL_HOST="mysql" \
    MYSQL_PORT="3306" \
    MYSQL_USER="root" \
    MYSQL_PASS="root" \
    MYSQL_DB="pdns" \
    PGSQL_HOST="postgres" \
    PGSQL_PORT="5432" \
    PGSQL_USER="postgres" \
    PGSQL_PASS="postgres" \
    PGSQL_DB="pdns" \
    SQLITE_DB="pdns.sqlite3"

RUN apk --update --no-cache add pdns pdns-backend-sqlite3 pdns-backend-bind pdns-backend-mysql pdns-backend-pgsql pdns-backend-random bash
RUN mkdir -p /etc/pdns/conf.d

EXPOSE 53/tcp 53/udp

ADD sql/* pdns.conf /etc/pdns/

ADD entrypoint.sh /bin/powerdns

ENTRYPOINT ["powerdns"]
