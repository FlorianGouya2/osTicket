Prérequis / informations à savoir avant de lancer le script :

_ Avoir téléchargé osTicket + extraire l'archive
_ le dossier osTicket doit contenir directement le dossier upload qui contient les dossiers et fichiers de osTicket (pas de sous dossier du style : osticket/osticket/upload)
_ le dossier osTicket doit contenir le fichier /upload/include/ost-sampleconfig.php et le dossier d'installation /upload/setup
 
_ avoir une VM Linux fonctionnelle
_ avoir une connexion Internet pour le téléchargement des paquets APT nécessaires au fonctionnement de osTicket

_ connaître l'emplacement du dossier osTicket (ex : /tmp/osticket) 
_ connaître l'emplacement de destination de osTicket (conseillé dans /var/www/html)

_ faire un apt update + apt upgrade
_ connaître la version de php actuellement disponible dans le dépot APT : cela servira dans le script car il faudra connaître le chemin exact du fichier php.ini
Exemple : pour une version de php 7.0, le fichier php.ini se trouvera dans /etc/php/7.0/apache2/ .
N.B : le script installera le paquet APT php s'il n'est pas déjà installé

_ droits d'exécution sur le script à mettre
_ script à lancer en tant que root



Description des fonctionnalités du script :

_ test si utilisateur = root
_ mise à jour dépôt paquets APT
_ installation des paquets APT nécessaires au fonctionnement de osTicket
_ demande du chemin source complet du dossier osTicket + vérification bonne saisie
_ vérification présence dossier /upload dans le dossier osTicket + fichier /upload/include/ost-sampleconfig.php + dossier /upload/setup
_ demande du chemin destination du dossier osTicket + vérification bonne saisie
_ demande nom du dossier osTicket (possibilité de renommer le dossier source)
_ test existence dossier osTicket : si oui -> suppression
_ copie du dossier osTicket du chemin source vers chemin destination
_ demande si package français : si oui -> demande chemin src + vérification bonne saisie + copie package dans dossier /upload/include/i18n/
_ demande si plugin : si oui -> demande chemin src + vérification bonne saisie + copie plugin dans dossier /upload/include/plugin/
_ copie du fichier /upload/include/ost_sampleconfig.php en /upload/include/ost-config.php
_ demande du chemin complet du fichier php.ini (exemple pour version php 7.0 : /etc/php/7.0/apache2/php.ini) + vérification bonne saisie 
_ utilisateur doit décommenter la ligne extension=mysqli dans fichier php.ini
_ changement du propriétaire dossier osTicket (propriétaire = www-data)
_ paramétrage des droits sur le fichier /upload/include/ost-config.php (u=rw,g=rw,o=rw)
_ demande si création de lien symbolique si dossier osTicket pas dans /var/www/html : si oui -> test existence lien symbolique (si oui -> suppression) + création lien symbolique
_ redémarrage du service apache2
_ demande nom de la base de données osTicket
_ demande nom de l'utilisateur de la base de données osTicket
_ demande mot de passe de l'utilisateur de la base de données osTicket
_ création et configuration de la base de données osTicket
_ attente installation graphique osTicket
_ reparamétrage des droits sur fichier /upload/include/ost-config.php (u=rw,g=r,o=r)
_ suppression du dossier d'installation de osTicket (/upload/setup)
_ affichage URL Support Center + URL connexion compte utilisateur + URL connexion compte technicien
