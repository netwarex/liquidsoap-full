FROM debian:unstable as deps

ENTRYPOINT bash

MAINTAINER The Savonet Team <savonet-users@lists.sourceforge.net>

ENV EXT_PACKAGES="camlimages gd graphics inotify sdl-liquidsoap ssl yojson"

USER root

# For libfdk-aac-dev
RUN sed -e 's#main#main contrib non-free#' -i /etc/apt/sources.list

RUN apt-get update && apt-get install -y --force-yes --no-install-recommends aspcud autoconf automake build-essential ca-certificates curl git pandoc unzip && \
    apt-get -y --force-yes autoclean && apt-get -y --force-yes clean

RUN curl -sL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh -o /tmp/install.sh && echo /usr/local/bin | sh /tmp/install.sh

RUN adduser opam

USER opam

WORKDIR /tmp

RUN git clone -b hlsfix https://github.com/netwarex/liquidsoap-full.git

WORKDIR /tmp/liquidsoap-full

RUN make init && make update

RUN opam init -y --disable-sandboxing --compiler=4.07.1 && opam update -y && opam install -y depext

RUN cat PACKAGES.default | grep '^ocaml' | cut -d'-' -f 2 | while read package; do \
      cd ocaml-$package && opam pin add --no-action . && cd ..; \
    done && cd liquidsoap && opam pin add --no-action .

RUN opam depext -y -l liquidsoap $EXT_PACKAGES `cat PACKAGES.default | grep '^ocaml' | cut -d'-' -f 2 | xargs echo` > /tmp/deps
      
USER root

RUN cat /tmp/deps | xargs apt-get install  -y --force-yes --no-install-recommends && \
    apt-get -y --force-yes autoclean && apt-get -y --force-yes clean 

USER opam

RUN eval $(opam config env) && opam install -y $EXT_PACKAGES

RUN eval $(opam config env) && \
  PACKAGES=`cat PACKAGES.default | grep '^ocaml' | cut -d'-' -f 2 | xargs echo` && \
    opam install -y liquidsoap $PACKAGES && opam uninstall liquidsoap $PACKAGES

FROM deps

ENTRYPOINT bash

MAINTAINER The Savonet Team <savonet-users@lists.sourceforge.net>

USER opam

WORKDIR /tmp/liquidsoap-full

RUN make update

RUN cp PACKAGES.default PACKAGES

RUN ./bootstrap

RUN eval $(opam config env) && ./configure && make clean && make && make doc

USER root

RUN eval $(opam config env) && make install
