# Créer un Dockerfile pour cette application en mode production
FROM rustlang/rust:nightly as builder

WORKDIR /usr/src/app
COPY . .

RUN cargo install --path .
RUN cp /usr/local/cargo/bin/blog ./blog
RUN cargo install diesel_cli --no-default-features --features postgres

CMD ["./blog"]