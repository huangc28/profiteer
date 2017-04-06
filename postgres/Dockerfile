FROM ubuntu:16.04

MAINTAINER Bryan Huang <huangchiheng@gmail.com>

# Install apt-repository-add command, it's not shipped with ubuntu.
# Install wget.
RUN apt-get update \
    && apt-get install -y python-software-properties software-properties-common wget \
    && add-apt-repository "deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main" \
    && wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
    && apt-get update \
    && apt-get install -y postgresql-9.6

# Change user to `postgre` inorder to execute PostgreSQL command.
USER postgres

# Spins up PostgreSQL server. create user `docker` with password `docker`
RUN /etc/init.d/postgresql start \
    && psql --command "CREATE USER docker WITH SUPERUSER PASSWORD 'docker';" \
    && createdb -O docker docker

# Set locale
ENV LANG en_US.utf8

# Adjust PostgreSQL configuration so that remote connections to the database are possible
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.6/main/pg_hba.conf

# And add ``listen_addresses`` to ``/etc/postgresql/9.6/main/postgresql.conf``
RUN echo "listen_addresses='*'" >> /etc/postgresql/9.6/main/postgresql.conf

#Add VOLUMEs to allow backup of config, logs and databases
VOLUME ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]

EXPOSE 5432

CMD ["/usr/lib/postgresql/9.6/bin/postgres", "-D", "/var/lib/postgresql/9.6/main", "-c", "config_file=/etc/postgresql/9.6/main/postgresql.conf"]

