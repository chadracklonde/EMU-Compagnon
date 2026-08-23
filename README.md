# EMU Compagnon

Application mobile Flutter pour l'Église Méthodiste Unie : Bible, Cantiques
« Chants de Victoire », Dictionnaire biblique, et (à venir) Liturgie EMU.

## Démarrage
```
flutter create . --project-name emu_compagnon   # si les dossiers android/ios manquent encore
flutter pub get
flutter run
```

## Nom d'affichage sur les appareils
Le nom technique du package est `emu_compagnon` (`pubspec.yaml`). Le nom
affiché à l'utilisateur, « EMU Compagnon », est déjà réglé dans
`lib/main.dart` (`MaterialApp.title`). Pour que ce nom apparaisse aussi
sous l'icône de l'app sur le téléphone, une fois les dossiers natifs générés :
- **Android** : `android/app/src/main/AndroidManifest.xml` → `android:label="EMU Compagnon"`
- **iOS** : `ios/Runner/Info.plist` → `CFBundleDisplayName` = `EMU Compagnon`

## Contenu inclus
- `assets/db/app_data.db` — Bible Louis Segond 1910 (31 102 versets), 444 cantiques
  "Chants de Victoire", 228 entrées de dictionnaire biblique, index FTS5 pour
  la recherche/concordance.
- Modules actifs : Bible (navigation livre/chapitre + concordance + étoile
  favoris par verset), Cantiques (liste + recherche + détail + étoile
  favoris), Dictionnaire biblique (liste alphabétique + recherche),
  Favoris (onglet dédié, versets et cantiques enregistrés, retrait en un tap),
  À propos (crédit développeur, contact, liens vers les ressources
  officielles UMC).
- Module Liturgie : pas encore construit (en attente du contenu).

## Icône de l'application
Le logo (croix et flamme, sur fond bordeaux #731932) est déjà dans
`assets/icons/` et configuré dans `pubspec.yaml` via `flutter_launcher_icons`.
Pour générer les icônes natives iOS/Android à partir de ce fichier unique :
```
flutter pub get
dart run flutter_launcher_icons
```
Cela crée automatiquement toutes les tailles nécessaires (y compris l'icône
adaptative Android, qui utilise `app_icon_foreground.png` — le motif seul,
fond transparent — posé sur le fond bordeaux `#731932`).

## Non testé dans cet environnement
Ce code a été écrit directement (pas de SDK Flutter disponible dans le
bac à sable où il a été généré). Avant de committer : `flutter pub get`
puis `flutter analyze` pour attraper d'éventuelles fautes de frappe, et
tester sur un simulateur ou appareil réel.

## Prochaines étapes suggérées
1. `flutter pub get` + `flutter run` pour valider
2. Régler le nom d'affichage natif (voir ci-dessus) + icône d'app
3. Ajouter les favoris/signets (table `bookmarks` déjà prête dans la DB)
4. Étoffer encore le dictionnaire si besoin
5. Ajouter le module Liturgie une fois le contenu prêt
