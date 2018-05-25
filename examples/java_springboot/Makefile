.PHONY: run watch test-unit test-functional test format style complexity


run: watch

watch: prepare
	mvn clean spring-boot:run

test-unit: prepare
	mvn clean test-compile surefire:test@unit

test-functional: prepare
	mvn clean test-compile surefire:test@functional

test: prepare
	mvn clean test

format: prepare
	mvn fmt:format

style: prepare
	mvn fmt:check

complexity: prepare
	mvn validate


prepare:
	./generate_maven_settings
	alias mvn="docker run --rm \
		-v `pwd`/src:/app/src \
		-v `pwd`/pom.xml:/app/pom.xml \
		-v `pwd`/settings.xml:/root/.m2/settings.xml \
		-v maven_cache:/root/.m2/repository \
		-p 8080:8080 \
		-w /app \
		maven:slim mvn"
