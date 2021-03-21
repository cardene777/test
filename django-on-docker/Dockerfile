# pull official base image
FROM python:3.8.2

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# create Django directory for the app user
ENV APP_HOME=/usr/src/web
RUN mkdir -p $APP_HOME && \
    mkdir $APP_HOME/static && \
    mkdir $APP_HOME/media

# set work directory
WORKDIR $APP_HOME

COPY . /usr/src/web

ENV POETRY_VERSION=1.0.10 \
    PATH="/root/.poetry/bin:$PATH"

RUN curl -sSL https://raw.githubusercontent.com/sdispater/poetry/${POETRY_VERSION}/get-poetry.py | python && \
    poetry config virtualenvs.create false

# install dependencies
COPY ./poetry/pyproject.toml ./poetry/poetry.lock ./

RUN poetry install

# copy entrypoint shell file
COPY web/entrypoint.sh $APP_HOME

# copy project
COPY web $APP_HOME

# chown all the files to the app user
#RUN chown -R app:app $APP_HOME

# run entrypoint shell file
ENTRYPOINT ["/usr/src/web/entrypoint.sh"]
