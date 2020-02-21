# DOCKER_BUG_LIST.md
Liste des problèmes courants et comment les résoudre...

## Sommaire
- [Utilisation de container Linux impossible](#utilisation-de-container-linux-impossible)
- [Démarrage de Docker impossible](#démarrage-de-docker-impossible)
- [Fichiers locaux inaccessibles](#fichiers-locaux-inaccessibles)
- [Docker ne tourne pas avec les droits administrateur](#docker-ne-tourne-pas-avec-les-droits-administrateur)
- [Port inaccessible](#port-inaccessible)
---
#### Utilisation de container Linux impossible
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
path\to\file\docker.exe: image operating system "linux" cannot be used on this platform.
See 'path\to\file\docker.exe run --help'.
```
Raison : Docker est *actuellement* configuré pour faire fonction des containers Windows.

Solution :
- Cliquer sur l'icone Docker de la barre des tâche.
- Appuyer sur 'Switch to Linux containers...'
- Appuyer sur 'Switch'

---
#### Démarrage de Docker impossible
Message d'erreur :
```console
>
```
Raison : La virtualisation du processeur est surement désactivée.

Solution :
- Eteindre complètement son PC. (Pas mettre en veille, **éteindre**)

- Pour un HP : 
  - Allumer le PC et appuyer plusieurs fois sur la touche 'esc'
  - Appuyez sur la touche 'F10' pour accéder à la configuration du BIOS. 
  - Appuyez sur la flèche droite de l'onglet de 'Configuration Système', sélectionnez 'Technologie de Virtualisation' et appuyez sur la touche 'Enter'. 
  
- Pour un Dell
  - Allumer le PC et appuyer plusieurs fois sur la touche 'F2'
  - Appuyez sur la flèche droite de l'onglet 'Avancé' et sélectionnez 'Virtualisation', puis appuyez sur la touche 'Enter'.
  - Sélectionnez 'Activated' et appuyez sur la touche 'Enter'.

- Pour un Acer / Asus
  - Allumer le PC et appuyer plusieurs fois sur la touche 'F2'
  - Appuyez sur la flèche droite de l'onglet de 'Configuration Système', sélectionnez 'Technologie de Virtualisation' et appuyez sur la touche 'Enter'.
  - Sélectionnez 'Activated' et appuyez sur la touche 'Enter'.
  
- Eteindre et rallumer le PC en suivant les commandes proposé en bas de l'écran.


---
#### Fichiers locaux inaccessibles
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
path\to\file\docker.exe: Error response from daemon: Mount denied:
The source path "WORKDIR" doesn't exist and is not known to Docker.
See 'path\to\file\docker.exe run --help'.
```
Raison : Le partage des disques C:/ et/ou D:/ n'est pas activé

Solution :
- Cliquer sur l'icone Docker de la barre des tâche.
- Appuyer sur 'Settings'.
- Appuyer sur 'Shared Drives' dans la colonne de gauche.
- Cocher les disques C:/ et D:/.
- Appuyer sur 'Apply' en bas.

---
#### Docker ne tourne pas avec les droits administrateur
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
error during connect: Get http://link/: open //./pipe/docker_engine:
The system cannot find the file specified. In the default daemon configuration on Windows, 
the docker client must be run elevated to connect. 
This error may also indicate that the docker daemon is not running.
```
Raison : Docker doit être lancé au moins une fois avec les droits d'administrateurs

Solution :
- Cliquer sur l'icone Docker de la barre des tâche.
- Appuyer sur 'Quit Docker Desktop'
- Faire un clic droit sur 'Docker Desktop' dans les programmes, et selectionner ('Plus')>'Run as administrator'

---
#### Port inaccessible
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
path\to\file\docker.exe: Error response from daemon: Ports are not available: 
/forwards/expose/port returned unexpected status: 500
```
Raison : Le port 8080 est déjà utilisé, soit par un autre container de Docker, soit par un autre processus

Solution :
- Vérifier que le container ne tourne pas déjà :
  ```console
  > docker ps
  ```
- Si un container tourne :
  - l'arreter :
    ```console
    > docker stop <CONTAINER ID>
    ```
  - Ré-exécuter la commande initiale :
    ```console
    > docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
    ```
- Sinon, changer le port sur lequel le container doit tourner :
  ```console
  > docker run -it -p 127.0.0.1:8081:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container'
  ```
