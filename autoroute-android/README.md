# L'AUTOROUTE — projet Android hors connexion

Application Android autonome (WebView locale) : le jeu, les cartes et les ressources sont embarqués dans l'APK. Aucune permission Internet n'est déclarée.

## Construire l'APK automatiquement

Le dépôt contient un workflow GitHub Actions (`.github/workflows/build-apk.yml`).

1. Crée un dépôt GitHub et importe le contenu de ce dossier.
2. Ouvre l'onglet **Actions** et lance **Build APK** (ou pousse un commit).
3. À la fin du workflow, télécharge l'artefact **Autoroute-debug-apk**.
4. Décompresse-le : `app-debug.apk` est installable sur les téléphones Android.

L'APK généré par cette méthode est un APK debug installable et partageable directement. Pour une publication Play Store, il faudra créer une clé de signature release.

## Construire localement

Avec Android Studio, Android SDK 35, JDK 17 et Gradle 8.9 :

```bash
gradle assembleDebug
```

L'APK sera dans `app/build/outputs/apk/debug/app-debug.apk`.

## Règles et fonctionnement

- 2 à 6 joueurs, 4 étapes par tour.
- As = 14, égalité à l'étape 3 = échec.
- Étape 4 : « entre » est strict ; égalité avec une borne = extérieur.
- Un paquet commun est utilisé entre les tours ; il est remélangé lorsqu'il reste moins de quatre cartes.
- Les données de la partie restent en mémoire pendant la session.

L'alcool n'est pas nécessaire pour jouer : les gorgées peuvent être remplacées par des points, des gorgées d'eau ou des défis. Ne conduisez jamais après avoir consommé de l'alcool.
