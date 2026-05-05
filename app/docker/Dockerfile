dockerfile:
FROM python:3.11-slim

# Criando usuário não-root
RUN useradd --create-home --shell /bin/bash appuser

# Diretório de trabalho
WORKDIR /app

# Copia requirements
COPY app/requirements.txt .

# Instala dependências
RUN pip install --no-cache-dir -r requirements.txt

# Copia código
COPY app/ .

# Usa usuário seguro
USER appuser

# Porta
EXPOSE 5000

# Comando inicial
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "--workers", "2", "app:app"]

