# Mon Prof IA – 3ème Année 🇩🇯

Application éducative Android pour la 3ème année primaire à Djibouti, basée sur une bibliothèque personnelle de guides CRIPEN.

## Modules
- Photo d'exercice (appareil photo ou galerie) et correction via un **serveur HTTPS** à configurer.
- Recherche dans les guides et lecteur PDF lorsque les fichiers sont fournis localement.
- Exercices interactifs et génération de variantes simples **hors ligne**.
- Lecture audio et dictées (selon les voix Android).
- Tableau de bord parental (données locales).
- Fonctionnement hors ligne des activités embarquées.

## APK automatique
Ouvrir **Actions > Android APK > Run workflow**. Quand le job est vert, télécharger l'archive **mon-prof-ia-apk** dans les *Artifacts* du run, la décompresser, puis installer app-debug.apk sur Android.

## Installation locale pour les développeurs
```bash
npm install
npm test
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```

## Guides CRIPEN
**Les guides PDF ne sont pas publiés dans ce dépôt public.** Pour usage personnel autorisé, copier les PDF dans `www/pdf/` et ajouter le catalogue approprié. Vérifier les droits de redistribution avant toute publication.

## Correction photo IA
Configurer dans l'onglet Photo l'URL d'un **serveur de correction HTTPS**, qui expose `POST /api/corriger` et accepte JSON `{image,matiere,guideId,page,note}`. Ce serveur protège la clé API OpenAI et doit activer CORS pour les origines Capacitor. **Aucune clé API dans le dépôt ni dans l'APK.** Sans serveur, la correction automatique des nouvelles photos n'est pas disponible.

## Limites
La recherche des guides dépend des fichiers/index fournis; la version publique inclut un petit catalogue d'exemple, pas les sept PDF. La lecture vocale dépend des voix installées sur l'appareil. APK non confirmé tant que GitHub Actions n'a pas terminé.
