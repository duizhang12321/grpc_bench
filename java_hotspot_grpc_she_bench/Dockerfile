FROM eclipse-temurin:19.0.2_7-jdk-focal

WORKDIR /app
COPY java_hotspot_grpc_sgc_bench /app
COPY proto/helloworld/helloworld.proto /app/src/main/proto/helloworld.proto

RUN /app/gradlew installDist

ENV GC "-XX:+UseShenandoahGC"
ENV JAVA_OPTS "${GC} -XX:MinRAMPercentage=70 -XX:MaxRAMPercentage=70"

ENTRYPOINT [ "/app/build/install/examples/bin/hello-world-server" ]

