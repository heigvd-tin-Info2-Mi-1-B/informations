# BUG_LIST.md
Liste des problèmes courants et comment les résoudre...

## Utilisation de container Linux impossible
Solution : La virtualisation du processeur est surement désactivée.

Pour la réactiver :
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
