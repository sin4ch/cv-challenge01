FROM python:3.11-slim
WORKDIR /app
RUN pip install poetry
COPY pyproject.toml poetry.lock /app/
RUN poetry config virtualenvs.create false
RUN poetry install
COPY . /app
ENV PYTHONPATH=/app:$PYTHONPATH  
EXPOSE 8000
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --reload --host 0.0.0.0"]
