# TEAM GRID V106 — Cloud Sync

## 1. Créer un projet Supabase
Crée un projet sur Supabase.

## 2. Installer les tables
Dans **SQL Editor**, colle et exécute `supabase_teamgrid_setup.sql`.

## 3. Activer l'authentification par e-mail
Dans Supabase > Authentication, laisse l'authentification e-mail activée.
Ajoute l'URL GitHub Pages de TEAM GRID dans les URLs de redirection autorisées.

## 4. Ouvrir TEAM GRID
Sur l'accueil, clique **☁ Synchronisation** puis renseigne :
- Project URL
- clé publique `anon` / publishable
- ton e-mail
- ton nom
- un code d'équipe partagé, par exemple `40KTASTROPHE`

Clique ensuite :
1. Enregistrer la configuration
2. Recevoir le lien de connexion
3. Ouvre le lien reçu par e-mail
4. Connecter l'équipe

Tous les coéquipiers utilisent le même code équipe.

## Sauvegarde
- Chaque modification est d'abord enregistrée dans `localStorage`.
- Après ~850 ms sans nouvelle modification, elle est envoyée dans Supabase.
- Les autres appareils reçoivent la mise à jour via Realtime.
- Chaque sauvegarde cloud crée une ligne dans `teamgrid_history`.
- Un conflit de version déclenche une récupération de la version cloud au lieu d'écraser silencieusement.

## Téléphone
Le mode téléphone tente :
1. plein écran,
2. verrouillage natif paysage,
3. rotation CSS de secours si le navigateur refuse le verrouillage.
