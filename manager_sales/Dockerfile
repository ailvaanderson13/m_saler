FROM python:3.10.7-buster

ENV PYTHONDONTWRITEBYTECODE=1

ENV PYTHONUNBUFFERED=1

ENV DEBIAN_FRONTEND=noninteractive

RUN : \
    && set -x \
    && apt-get update -y \
    && apt-get upgrade -y \
    # && apt-get install -y --no-install-recommends python-is-python3 python3-venv \
    && apt-get autoremove --yes \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && rm -rf /usr/share/doc /usr/share/man \
    && :

WORKDIR /code/

COPY requirements.txt .

ENV VIRTUAL_ENV=/opt/venv
ENV PATH=$VIRTUAL_ENV/bin:$PATH
RUN python -m venv $VIRTUAL_ENV

RUN pip install -r requirements.txt

COPY . .

ENTRYPOINT [ "./docker-entrypoint.sh" ]


# COPY . /code/
