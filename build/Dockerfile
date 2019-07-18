FROM rust:1.35 as builder

RUN set -ex && \
    apt-get update && \
    apt-get --no-install-recommends --yes install \
    clang \
    libclang-dev \
    llvm-dev \
    libncurses5 \
    libncursesw5 \
    cmake \
    git

WORKDIR /usr/src/grin

COPY grin .

RUN cargo build --release

FROM debian:9.4

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y locales openssl

RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=en_US.UTF-8

ENV LANG en_US.UTF-8

COPY --from=builder /usr/src/grin/target/release/grin /usr/local/bin/grin

WORKDIR /root/.grin

RUN grin server config && \
    sed -i -e 's/run_tui = true/run_tui = false/' grin-server.toml && \
    sed -i -e 's/stdout_log_level = \"Warning\"/stdout_log_level = \"Info\"/' grin-server.toml && \
    sed -i -e 's/log_to_file = true/log_to_file = false/' grin-server.toml && \
    sed -i -e 's/api_http_addr = \"127.0.0.1:3413\"/api_http_addr = \"0.0.0.0:3413\"/' grin-server.toml

VOLUME ["/root/.grin"]

EXPOSE 3413 3414 3415 3416

ENTRYPOINT ["grin"]

CMD ["server", "run"]
