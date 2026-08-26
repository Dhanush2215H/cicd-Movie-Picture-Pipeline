FROM public.ecr.aws/docker/library/python:3.10-slim
ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /app

RUN pip install pipenv gunicorn

COPY Pipfile* ./
RUN pipenv install --system --ignore-pipfile

COPY . .

EXPOSE 5000

CMD ["gunicorn", "-b", "0.0.0.0:5000", "--chdir", "/app", "wsgi:app"]