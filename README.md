# Dockers pour Symfony

L'ensemble des Dockers sont montés grâce à [Docker Compose version 3](https://docs.docker.com/compose/compose-file/) 
et sont fournis avec un fichier Makefile afin de faciliter leur utilisation.

## Usage

Afin d'installer et utiliser ces Docker, deux commandes sont nécessaires et devront être lancées à la 
racine de votre projet.

```
# Construction de l'image Docker
make build
# Lancement de l'image
make up
```
Il existe également plusieurs autres commandes qui sont toutes consultablent dans le fichier "Makefile'" des Dockers 
présent dans le dépôt.

<br>

**Remarque :** Par défaut l'ip de votre serveur sera `172.23.0.10`. Cependant cette IP peut très bien être changer dans 
le fichier 'docker-compose.yml' en modifiant la ligne `ipv4_address: 172.23.0.10` du service nginx.

## Nginx `php7.1.4/ directory`

### Stack Technologique

- Language : [PHP 7.1.4](http://php.net/)
- Server web : [Nginx](https://nginx.org/en/)
- Extras :
    - [Bower](https://bower.io/)
    - [Gulp](http://gulpjs.com/)
    - [Phpunit](https://phpunit.de/)
    - [PhpCs Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)
    - [Phploc](https://github.com/sebastianbergmann/phploc)
    - [Pdepend](https://pdepend.org/)
    - [Phpmd](https://phpmd.org/)
    - [Phpcpd](https://github.com/sebastianbergmann/phpcpd)