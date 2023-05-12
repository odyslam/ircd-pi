FROM rust:slim

RUN apt-get update && apt-get install -y git make jq gcc pkg-config libmpg123-dev && rustup target add wasm32-unknown-unknown
RUN git clone https://github.com/odyslam/darkfi
WORKDIR ./darkfi
RUN make BINS=ircd
RUN mkdir -p /usr/local/bin && cp /darkfi/ircd /usr/local/bin/ircd && chmod +x /usr/local/bin/ircd
COPY run.sh /usr/local/bin/run.sh 
RUN chmod +x /usr/local/bin/run.sh
ENTRYPOINT /usr/local/bin/run.sh
