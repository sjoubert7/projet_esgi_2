# Préparation de l'environnement de travail pour l'application

# Environnement du language installer sur le système & la version
FROM python:3.6-alpine

#Dossier de travail
WORKDIR /opt

# Liens des sites
ENV ODOO_URL= "http://odoo.local"
ENV PGADMIN_URL= "http://pgadmin.local"

# Execution du programme
RUN pip install flask==1.1.2

# Copie des informations à la racine
COPY app.py .

# Port utilisé pour l'application
EXPOSE 8080

# Point d'entrée du language
ENTRYPOINT ["python", "app.py"]