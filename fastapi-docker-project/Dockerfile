FROM python:3.13-slim

WORKDIR /app

# Instala o Poetry
RUN pip install --upgrade pip && \
    pip install poetry

# Copia os arquivos de dependência
COPY pyproject.toml poetry.lock ./

# Instala as dependências do projeto
RUN poetry config virtualenvs.create false && \
    poetry install --no-interaction --no-ansi --no-root

# Copia o código da aplicação
COPY ./app /app

# Expõe a porta e roda o servidor
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]