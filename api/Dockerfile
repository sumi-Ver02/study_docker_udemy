FROM gradle:7 AS base
CMD ["bash"]

# build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# prod
FROM openjdk:17 AS prod
COPY --from=build /workspace/build/libs/api-0.0.1-SNAPSHOT.jar ./api.jar
CMD [ "java", "-jar", "api.jar" ]