# Plan de continuité des projets — mode gratuit (14/10/2026)

Objectif : conserver des services disponibles, sauvegardés et testables sans dépendre d'un abonnement ChatGPT payant.

> **Ce document est un plan, pas une certification de bon fonctionnement.** Un déploiement « READY » ou une base « ACTIVE_HEALTHY » ne garantit ni la connexion des utilisateurs ni l'installation d'un APK.

## Inventaire confirmé en lecture seule

- GitHub organisation `Nexus-tech-01` : `NexTelegrambots`, `Site-officiel-`, `.github`, `Project-02`, `demo-repository`.
- GitHub personnel `Tresor562` : `knowMe_mpv` (monorepo API, Web et Expo mobile), `knowMe-`, `knowMe_secret` et d'autres projets.
- Vercel : `knowme-android`, `nexcontrol-nexus-vps`, `nexai-connect-v2`, `nexus-tech-official`, `tresor-hontonnou-portfolio`.
- Supabase : `NexCode`, `KnowMe Friends` (déclarés sains à l'inventaire, mais vérification fonctionnelle requise).
- VPS : accès terminal et santé des services **non vérifiés** dans cet inventaire.

## Priorités

1. **P0 :** sécuriser accès, données, sauvegardes, budget, authentification KnowMe et pairing NexAI ; vérifier la disponibilité du VPS et de NexControl.
2. **P1 :** stabiliser l'API, les médias, les conversations, les tests Web/Android et la production ; une seule version identifiée par SHA.
3. **P2 :** supervision indépendante de ChatGPT, alertes anti-doublons, redémarrages contrôlés, restauration périodiquement testée.
4. **P3 :** nouvelles fonctions, bots secondaires et NexPlayer après stabilisation du cœur.

## Organisation technique

- **Ne pas recréer aveuglément des pipelines :** `Tresor562/knowMe_mpv` possède déjà `ci.yml`, des jobs APK, une release gate et un contrôle de runtime ; `Nexus-tech-01/NexTelegrambots` possède des workflows CI, déploiement et diagnostic nombreux. Auditer déclencheurs et coûts d'abord.
- Corrections dans des branches courtes, PR, CI (lint, types, tests, build) et smoke test avant production. Pas de déploiements concurrents ; conserver rollback et version de secours.
- Traiter ensemble compatibilité Web/API/Android, migrations de base et version installable ; une page Web Vercel ne représente pas une APK vérifiée.
- Au VPS : services managés, redémarrage uniquement sur erreurs récupérables avec temporisation, endpoints de santé, alertes privées. Ne jamais boucler sur erreurs de connexion ou de quota.
- Sauvegardes chiffrées hors serveur, rotations, test de restauration ; secrets hors Git, permissions minimales, 2FA, vérification RLS des données exposées.
- Surveiller **facturation et quotas** : le forfait ChatGPT n'assure pas la gratuité de Vercel, Render, Supabase, VPS, API ou stockage.

## Mode de travail scolaire

- Se concentrer sur les incidents P0/P1 ; traiter les améliorations pendant deux petites séances hebdomadaires plutôt que surveiller les bots en permanence.
- Conserver en ticket : dépôt, branche/commit, erreur expurgée, résultat attendu, étapes de reproduction, tests et preuve de correction.
- Si les outils directs GitHub/VPS ne sont plus accessibles en ChatGPT Free : travailler avec des patchs, PR et commandes reproductibles, sans jamais exposer de jetons ni mots de passe.

## Preuves à obtenir avant d'affirmer que tout fonctionne

- [x] Dépôts GitHub, Vercel et Supabase visibles recensés.
- [x] Workflows existants identifiés dans KnowMe et NexTelegrambots.
- [ ] Coûts, quotas, domaines et branches de production audités.
- [ ] VPS atteint via canal d'administration sécurisé ; services et logs vérifiés.
- [ ] Sauvegarde de données réellement restaurée.
- [ ] Connexion, messagerie et envoi de médias KnowMe testés de bout en bout.
- [ ] Pairing NexAI réel validé.
- [ ] APK compilée, récupérée et installée sur téléphone.
- [ ] Alertes et reprise simulées et vérifiées.

Une version plus détaillée, avec calendrier et fiches d'incident, peut être conservée séparément.
