FROM ubuntu:xenial

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    curl \
    libldap2-dev \
    libncurses5-dev \
    libpam0g-dev \
    libssl-dev \
    strace

ADD pine4.64.tar.bz2 /
COPY *.patch /
RUN patch -p0 < rules.patch \
    && patch -p0 < incoming.patch \
    && patch -p0 < fromheader.patch \
    && patch -p0 < searchheader.patch \
    && patch -p0 < maildir.patch \
    && cd /pine4.64 \
    && ./build SSLLIB=/usr/lib ldb \
    && cp bin/* /usr/local/bin \
    && cd / \
    && rm -rf pine4.64 *.patch \
    && rm -rf /var/lib/apt/lists/*

CMD ["pine", "-p", "{mail.messagingengine.com/user=iansealy@fastmail.fm/ssl}inbox.remote_pinerc"]
