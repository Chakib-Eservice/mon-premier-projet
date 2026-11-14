# Chakib E-Service — site web

Site vitrine de **Chakib E-Service** (Constantine) : services administratifs et numériques.

Site statique sans build : `index.html` contient le HTML, le CSS (balise `<style>`), le JavaScript (balise `<script>`) et le favicon.
Les photos sont dans `images/`. Netlify publie la racine du dépôt (`netlify.toml`).

Palette : **noir et bleu profond uniquement** (variables `--bg`, `--blue-*` en haut de la balise `<style>`).

| Photo (`images/`)                    | Utilisée dans                      |
|--------------------------------------|------------------------------------|
| `facade-e-service-ali-mendjeli.jpg`  | Hero, galerie, image de partage    |
| `espace-bureau-interieur.jpg`        | Hero (vignette), galerie, bandeau contact |
| `vitrine-services.jpg`               | Section services, galerie          |
| `boutique-e-service-entree.jpg`      | Section « Le bureau », galerie, footer |
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

## SEO local (avancé)
- **JSON-LD `@graph`** dans le `<head>` : `LocalBusiness`/`InternetCafe` (adresse Cosider, Nouvelle Ville, Ali Mendjeli, téléphone +213542522033, logo, photos, zone desservie, catalogue de services), `WebSite`, `WebPage` et `FAQPage` (identique à la section FAQ visible).
- **Meta** : description et mots-clés locaux (FR + AR), `robots`, `canonical`, `hreflang`, Open Graph et Twitter Card avec la photo de la façade, géolocalisation `DZ-25`.
- **Fichiers** : `robots.txt` et `sitemap.xml` (avec les photos). Après la mise en ligne, soumettez `https://chakibeservice.netlify.app/sitemap.xml` dans Google Search Console.
- **Avis clients** : la note 5,0 est affichée sur la page. Pour afficher de vrais avis, copiez-les depuis la fiche Google dans la liste `REVIEWS` (script en bas de `index.html`) : `{ name: 'Prénom N.', date: 'il y a 2 semaines', text: '…' }`. La note n'est volontairement pas balisée en `aggregateRating` (Google ignore et peut pénaliser les avis auto-déclarés d'une entreprise sur son propre site).
- **Horaires / coordonnées GPS** : non renseignés faute d'information. À ajouter dans le JSON-LD (`openingHoursSpecification`, `geo`) dès qu'ils sont connus, à l'identique de la fiche Google.

## Fond animé « carte numérique »
Généré en JavaScript (fin du `<script>` dans `index.html`, bloc *Digital city-map background*) sous forme d'un SVG en ligne : rues, îlots, axes principaux lumineux, nœuds et hubs pulsants, et quelques « véhicules » lumineux qui circulent sur les routes.
- La carte est dessinée une seule fois ; seuls la position du calque (dérive lente + léger parallaxe souris) et les véhicules bougent, via `transform`/`opacity` (composités par le GPU).
- Moins d'éléments sur mobile, pause quand l'onglet est caché, image fixe si l'utilisateur a activé « réduire les animations ».
- Couleurs : bleu profond et noir uniquement. Réglages : `step` (taille des îlots), nombre de véhicules (`n`), opacités dans le gabarit SVG.

## Blog / Articles (arabe) et pages d'information
- **Page Blog** : `articles/index.html` (liste de tous les articles) ; aperçu des 6 articles dans la section `#blog` de l'accueil.
- **Articles** (RTL, sommaire, barre de lecture, balisage `BlogPosting` + `BreadcrumbList`) :
  - `guide-demarches-administratives-en-ligne-algerie.html`, `guide-progres-campus-france.html`,
  - `guide-paiement-electronique-edahabia-baridimob.html`, `guide-cv-ats.html`,
  - `guide-dossier-visa-schengen.html`, `guide-numerisation-documents-pdf.html`.
- **Pages** : `a-propos.html`, `contact.html`, `politique-de-confidentialite.html` (même en-tête et pied de page partout : Accueil · Blog · À propos · Contact · Politique de confidentialité).
- Styles et script partagés : `assets/blog.css`, `assets/blog.js`.
- Ajouter un article : copier un fichier de `articles/`, changer titre, description, `canonical`, JSON-LD et contenu ; ajouter sa carte dans `articles/index.html` et dans `#blog` de l'accueil, dans le nœud `Blog` du JSON-LD de l'accueil et dans `sitemap.xml`.
- Les démarches évoluent : relire les articles chaque année (dates, plateformes officielles).

## Performance
- **Polices auto-hébergées** dans `assets/fonts/` (sous-ensembles latin + arabe, `font-display: swap`, préchargement des polices du titre) : plus aucune requête vers Google Fonts.
- **Images WebP responsives** (`images/*-480|800|1200.webp`) via `<picture>` + `srcset`/`sizes` ; les JPG d'origine restent en secours et pour les aperçus de partage. Pour une nouvelle photo : générer les variantes WebP aux mêmes largeurs.
- **Rendu** : `content-visibility: auto` sur les sections hors écran ; sur mobile/tactile, pas de flou d'arrière-plan en direct ni d'effet de flou à l'apparition (même rendu visuel, beaucoup moins coûteux).
- **Animations** : uniquement `transform`/`opacity` (composées par le GPU) ; le fond « carte » démarre après le chargement, quand le navigateur est inactif, à ~30 i/s, et se met en pause si l'onglet est masqué ou en mode économie de données.
- **Cache** (`netlify.toml`) : polices 1 an (immutable), CSS/JS 7 jours (versionnés avec `?v=`), images 30 jours. Après une modification de `assets/blog.css` ou `assets/blog.js`, incrémenter `?v=` dans les pages.
