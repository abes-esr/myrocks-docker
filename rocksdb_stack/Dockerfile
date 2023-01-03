FROM mariadb:10.3-focal
RUN apt-get -y update && \
    apt-get install apt-transport-https curl -y && \
    curl -o /etc/apt/trusted.gpg.d/mariadb_release_signing_key.asc 'https://mariadb.org/mariadb_release_signing_key.asc' && \
    sh -c "echo 'deb https://mirrors.ircam.fr/pub/mariadb/repo/10.3/ubuntu focal main' >>/etc/apt/sources.list" && \
    apt-get -y update && \
    apt-get install mariadb-plugin-rocksdb -y && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*
