FROM aspireorg/federatednode

MAINTAINER Aspire Developers <admin@aspirecrypto.com>

# install gasp
ENV ASPIREGAS_VER="1.0.0"
WORKDIR /tmp
# COPY gasp-x86_64-unknown-linux-gnu.tar.gz /tmp/
RUN wget -O gasp-x86_64-unknown-linux-gnu.tar.gz https://github.com/AspireOrg/gAsp/releases/download/v${ASPIREGAS_VER}/gasp-x86_64-unknown-linux-gnu.tar.gz
RUN mkdir -p /tmp/gasp-x86_64-unknown-linux-gnu/
RUN tar -xvzf gasp-x86_64-unknown-linux-gnu.tar.gz -C /tmp/gasp-x86_64-unknown-linux-gnu/
RUN install -C -m 755 -o root -g root --backup=off gasp-x86_64-unknown-linux-gnu/* /usr/local/bin/
RUN rm gasp-x86_64-unknown-linux-gnu.tar.gz && rm -rf gasp-x86_64-unknown-linux-gnu

# Set up gaspd dirs and files
RUN mkdir -p /root/.gasp/
COPY gasp.conf /root/.gasp/
COPY start.sh /usr/local/bin/start.sh
RUN chmod a+x /usr/local/bin/start.sh

EXPOSE 9874 11374 19874 22485

# NOTE: Defaults to running on mainnet, specify -e TESTNET=1 to start up on testnet
ENTRYPOINT ["start.sh"]
