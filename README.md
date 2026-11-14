# Chakib E-Service — site web

Site vitrine de **Chakib E-Service** (Constantine) : services administratifs et numériques.

Site statique sans build : `index.html` contient le HTML, le CSS (balise `<style>`), le JavaScript (balise `<script>`) et le favicon.
Les photos sont dans `images/`. Netlify publie la racine du dépôt (`netlify.toml`).

Palette : **noir et bleu profond uniquement** (variables `--bg`, `--blue-*` en haut de la balise `<style>`).

| Photo (`images/`)                    | Utilisée dans                      |
|--------------------------------------|------------------------------------|
| `facade-e-service-ali-mendjeli.jpg`  | Hero, galerie, image de partage    |
| `espace-bureau-interieur.jpg`        | Hero (vignette), galerie           |
| `vitrine-services.jpg`               | Section services, galerie          |
| `boutique-e-service-entree.jpg`      | Galerie, bandeau contact, footer   |
| `poste-de-travail.jpg`               | Galerie                            |

Pour ajouter une photo : l'optimiser (≈1400 px, JPG qualité 80) et ajouter un bouton `.ph` dans la galerie.

## Liens officiels
- WhatsApp : https://wa.me/213542522033
- Instagram : https://www.instagram.com/chakib_e.service/
- TikTok : https://www.tiktok.com/@chakib_e.service
- Facebook : https://www.facebook.com/eservice.chakib

## Modifier
- Couleurs : variables dans `:root` en haut de la balise `<style>` : noir `--bg`, bleu profond `--navy` / `--blue`, accent rouge `--red`.
- Messages WhatsApp pré-remplis : paramètre `?text=` de chaque lien `wa.me` dans index.html.

## Aperçu local
```bash
python3 -m http.server 8000
```

## Google Business Profile & SEO local
- **Données structurées** : bloc JSON-LD `LocalBusiness` / `InternetCafe` dans le `<head>` (nom, adresse Cosider, Nouvelle Ville, Ali Mendjeli, Constantine, téléphone, site, réseaux, services). À tester sur https://search.google.com/test/rich-results
- **Lien de la fiche Google** : dans le `<script>` en bas de `index.html`, constante `GBP` :
  - `url` → collez le lien de partage de la fiche (Google Maps → Partager, ex. `https://maps.app.goo.gl/...`) ; tous les boutons « Avis Google », « Google Maps » et la galerie l'utilisent.
  - `placeId` → (optionnel) active le lien direct « Laisser un avis ».
  - Mettez aussi ce lien dans `"hasMap"` du JSON-LD.
- Gardez exactement le même nom, adresse et téléphone sur le site, la fiche Google et les réseaux (cohérence NAP).
