FROM amd64/eclipse-temurin:17-jdk

COPY ./build/libs/global-0.0.1-SNAPSHOT.jar global-sookmyung.jar

ENV SPRING_PROFILES_ACTIVE=dev

CMD ["java", "-Dspring.profiles.active=${SPRING_PROFILES_ACTIVE}", "-jar", "global-sookmyung.jar"]