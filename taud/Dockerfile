FROM rust:slim

RUN apt-get update && apt-get install -y git make jq gcc pkg-config libmpg123-dev && rustup target add wasm32-unknown-unknown
RUN git clone https://github.com/odyslam/darkfi
WORKDIR ./darkfi
RUN make BINS=taud
RUN mkdir -p /usr/local/bin && cp /darkfi/taud /usr/local/bin/taud && chmod +x /usr/local/bin/taud
COPY run.sh /usr/local/bin/run.sh 
RUN chmod +x /usr/local/bin/run.sh
ENTRYPOINT /usr/local/bin/run.sh
