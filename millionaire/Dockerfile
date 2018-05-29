
FROM frolvlad/alpine-python-machinelearning
MAINTAINER sollsharp@gmail.com

WORKDIR /app

RUN apk update
RUN apk upgrade

RUN apk add --update alpine-sdk
RUN apk add python3-dev
RUN apk add build-base # GCC, libc-dev and binutils packages
RUN apk add mpfr-dev # bigfloat's requirements
RUN apk add gmp-dev # bigfloat's requirements

RUN pip3 install -U pip

COPY /requirements.txt ./
RUN pip3 install -r ./requirements.txt

COPY . .

CMD [ "python3", "./millionaire.py"]
