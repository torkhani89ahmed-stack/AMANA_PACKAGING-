# AMANA PACKAGING – Application Android

Application de gestion (dépôt, ventes, clients, factures, devis, bons de commande)
empaquetée en APK avec Capacitor. L'APK est compilé automatiquement par GitHub Actions.

## Obtenir l'APK

1. Créez un dépôt sur GitHub et envoyez-y **tout le contenu de ce dossier**
   (y compris le dossier `.github`).
2. Ouvrez l'onglet **Actions** : le workflow « Build APK » démarre tout seul
   (environ 5 minutes). Sinon : Actions → Build APK → **Run workflow**.
3. Une fois terminé (coche verte), ouvrez l'exécution et téléchargez
   **AMANA-PACKAGING-apk** en bas de page (fichier zip contenant `AMANA-PACKAGING.apk`).
4. Copiez l'APK sur le téléphone et installez-le
   (autorisez « Installer des applications inconnues » si Android le demande).

### APK dans l'onglet Releases (optionnel)

```bash
git tag v1.0.0
git push origin v1.0.0
```

L'APK est alors aussi publié dans **Releases**.

## Mettre à jour l'application

Modifiez `www/index.html`, envoyez le changement sur GitHub : un nouvel APK est compilé.
Les données (stock, ventes, factures) sont stockées sur le téléphone et sont conservées
lors d'une mise à jour, tant que l'application n'est pas désinstallée.

## Notes

- L'APK est signé en mode debug : il s'installe directement sur un téléphone.
  Pour une publication sur le Play Store, une signature release sera nécessaire.
- Le bouton Retour du téléphone suit la navigation de l'application
  (sous-onglet → onglet → accueil → confirmation avant de quitter).
- Notifications : l'APK utilise le plugin Capacitor Local Notifications. Dans Réglages,
  activez « Notification sur cet appareil » et acceptez l'autorisation demandée par Android.
  Une notification part quand un article passe en rupture ou sous son seuil.
  Elle ne peut pas partir si l'application est fermée (cela demanderait un serveur).
- Le bouton « Télécharger » des factures peut ne pas être disponible dans l'APK.

## Structure

```
www/index.html                  application
package.json                    dépendances Capacitor (dont notifications)
capacitor.config.json           nom et identifiant (tn.amana.packaging)
.github/workflows/build-apk.yml compilation automatique de l'APK
```
