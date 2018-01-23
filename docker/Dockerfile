FROM python:3.6.2-alpine3.6

LABEL maintainer="Fernando Possebon possebon@gmail.com"

# Environments
ENV TIMEZONE            America/Sao_Paulo
# Change the timezone
RUN apk add --update --no-cache tzdata \
    ffmpeg freetds freetds-dev g++ make fontconfig git \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    && echo "${TIMEZONE}" > /etc/timezone

# Install Forego
ADD https://github.com/jwilder/forego/releases/download/v0.16.1/forego /usr/local/bin/forego

RUN mkdir /app \
    && chmod u+x /usr/local/bin/forego

ADD requirements.txt /app
WORKDIR /app

RUN pip install -r requirements.txt

EXPOSE 3501
ENTRYPOINT ["tail", "-f", "/dev/null"]