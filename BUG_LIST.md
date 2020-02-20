# BUG_LIST.md
Liste des problèmes courants et comment les résoudre...

## Sommaire
* [Utilisation de container Linux impossible](#utilisation-de-container-linux-impossible)
* [Démarrage de Docker impossible](#démarrage-de-docker-impossible)
* [Fichiers locaux inaccessibles](#fichiers-locaux-inaccessibles)
  
## Utilisation de container Linux impossible
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container\'
path\to\file\docker.exe: image operating system "linux" cannot be used on this platform.
See 'path\to\file\docker.exe run --help'.
```
Raison : Docker est *actuellement* configuré pour faire fonction des containers Windows.

Solution :
- Cliquer sur l'icone Docker de la barre des tâche.
- Appuyer sur 'Switch to Linux containers...'
- Appuyer sur 'Switch'

## Démarrage de Docker impossible
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


## Fichiers locaux inaccessibles
Message d'erreur :
```console
> docker run -it -p 127.0.0.1:8080:8080 -v 'WORKDIR:path\to\dir' -v 'WORKDIR:path\to\dir' 'container\'
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
