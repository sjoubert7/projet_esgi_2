# Base image de l'application
FROM python:3.11-slim AS base

# Ajouter un check curl
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl && \
    rm -rf /var/lib/apt/lists/*

# Définir le dossier
WORKDIR /usr/local/app

# Installation des outils
COPY requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# base pour appliquer un environnement
FROM base AS dev
RUN pip install watchdog
ENV FLASK_ENV=development
CMD ["python", "app.py"]

# Définir le socle de la prod
FROM base AS final

# Copier les fichiers à la racine
COPY . .

# port exposer
EXPOSE 80

# Commande a exécuter
CMD ["gunicorn", "app:app", "-b", "0.0.0.0:80", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]
