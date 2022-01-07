ARG BUILD_FROM
FROM $BUILD_FROM as builder

LABEL maintainer="jannes"

RUN apk add rust
RUN apk add cargo
RUN apk add git
RUN git clone https://github.com/Hypercookie/qrcode.show qrcode
RUN cd qrcode && cargo build --release
RUN apk add ca-certificates tzdata

FROM $BUILD_FROM
RUN apk add libgcc
EXPOSE 8080
COPY --from=builder /qrcode/target/release/axum-server axum-server
CMD ["./axum-server"]

