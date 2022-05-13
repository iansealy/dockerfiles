FROM ubuntu:focal

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    libkrb5-dev \
    libldap2-dev \
    libncurses-dev \
    libpam0g-dev \
    libssl-dev

ADD alpine-2.25.tar.xz /
COPY *.patch /
RUN patch -p0 < rules.patch \
    && patch -p0 < compose.patch \
    && patch -p0 < fillpara.patch \
    && patch -p0 < fromheader.patch \
    && patch -p0 < insertpat.patch \
    && patch -p0 < longurl.patch \
    && patch -p0 < maildir.patch \
    && patch -p0 < outgoing.patch \
    && patch -p0 < tome.patch \
    && cd alpine-2.25 \
    && ./configure --enable-quotas --with-passfile=.alpine \
    && make \
    && cp alpine/alpine /usr/local/bin \
    && cd / \
    && rm -rf alpine-2.25 *.patch \
    && rm -rf /var/lib/apt/lists/*

CMD ["alpine", "-p", "{outlook.office365.com/ssl/user=bty107@qmul.ac.uk/auth=xoauth2}remote_pinerc"]
