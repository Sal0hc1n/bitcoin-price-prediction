FROM frolvlad/alpine-python3

WORKDIR /okcoin

RUN pip3 install -U pip

COPY requirements.txt ./
RUN pip3 install -r ./requirements.txt

COPY . .

CMD [ "python3", "./okcoin.py" ]
