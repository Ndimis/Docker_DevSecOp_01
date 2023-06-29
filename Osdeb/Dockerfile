#L'instruction 'FROM' pour utiliser l'image de base ici Debian la version 9
FROM debian:latest

#L'instruction 'RUN' permet d'éxécuter des commande dans notre conteneur
RUN apt-get update -yq \
&& apt-get install curl gnupg -yq \
&& curl -sL https://deb.nodesource.com/setup_16.x | bash \
&& apt-get install nodejs -yq \
&& apt-get clean -y

# L' instruction 'ADD' afin de copier ou de télécharger des fichiers dans l'image. 
#Dans notre cas, nous l'utilisons pour ajouter les sources 
#de notre application locale dans le dossier /app/ de l'image
ADD . /app/

#L'instruction 'WORKDIR' qui permet de modifier le répertoire courant. 
#La commande est équivalente à une commande 'cd' en ligne de commande. 
#L'ensemble des commandes qui suivront seront toutes exécutées depuis le répertoire défini
WORKDIR /app

#COPY package.json package-lock.json ./
#Ici 'RUN' va installer le package du projet Node.js
RUN npm install

#L'instruction 'EXPOSE' 
#permet d'indiquer le port sur lequel votre application écoute.
EXPOSE 2368

#L'instruction 'VOLUME' 
#permet d'indiquer quel répertoire vous voulez partager avec votre host
VOLUME /app/logs

#L'instruction 'CMD' . Celle-ci permet à notre conteneur 
#de savoir quelle commande il doit exécuter lors de son démarrage
CMD rpm run start