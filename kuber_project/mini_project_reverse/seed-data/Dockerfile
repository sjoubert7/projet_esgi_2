# Image source
FROM python:3.9-slim

# Installation du service Apache
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    apache2-utils \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /seed

COPY . .

# créer la base de donnée
RUN python make-data.py

CMD ["/seed/generate-votes.sh"]
