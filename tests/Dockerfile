# Build Stage
FROM ubuntu:noble

RUN apt-get update -q && \
    apt-get install -y build-essential cmake && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /usr/local/src
COPY . .

RUN cmake -S . -B build -DBUILD_TESTING=ON -DENABLE_WEBSOCKET=ON && \
    cmake --build build --target i2c-pololu-tests && \
    cmake --build build --target websocket-tests

WORKDIR /usr/local/src/build

CMD ["ctest", "--output-on-failure"]
