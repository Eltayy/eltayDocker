
<h1 align="center">Docker Php Nginx MariaDB Xdebug</h1>

## Installation du projet

- Configurer le .env
```sh
  cp .env.dist .env
```

- Configurer la conf nginx
```sh
  cp docker/nginx.default.conf.dist docker/nginx.default.conf
```

- Ajouter dans son hosts :
```sh
  127.0.0.1 PROJECT_NAME.local
```
> Mac & Linux  : /etc/hosts 

> Windows : C:\windows\system32\drivers\etc\hosts

- Lancer :
```sh
  docker compose up -d
```

## Configuration de xDebug 3 (VSCODE) :

- Installer l'extension PHP Debug
- Puis placer dans le fichier launch.json

```sh
  {
      "name": "Listen for Xdebug",
      "type": "php",
      "request": "launch",
      "hostname": "host.docker.internal",
      "port": 9003,
      "pathMappings": {
          "/var/www/html/": "${workspaceFolder}/www"
      }
  }
```
## Environnement
| Package | Version |
| ------ | ------ |
| Nginx | 1.25.1 |
| MariaDB | 11.0.2 |
| Php | 8.2.8 |
| xDebug | 3.2.2 |

## Infos
| Protocole | PORT |
| ------ | ------ |
| HTTP | 80 |
| Database | 3306 |