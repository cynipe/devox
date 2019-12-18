FROM python:3.7-alpine

RUN set -x \
  && apk upgrade --no-cache \
  && apk add --no-cache coreutils bash tzdata jq \
  && cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
  && apk del tzdata \
  && rm -rf /var/cache/apk/*

ENV AWS_SAM_CLI_VERSION 0.38.0
RUN apk add --no-cache --virtual build-deps gcc musl-dev \
  && pip install --no-cache-dir aws-sam-cli==$AWS_SAM_CLI_VERSION awscli \
  && apk del build-deps \
  && rm -rf /var/cache/apk/*


ENTRYPOINT ["sam"]
CMD []
