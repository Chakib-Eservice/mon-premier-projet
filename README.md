# Chakib E-Service — site web

Site vitrine de **Chakib E-Service** (Constantine) : services administratifs et numériques.

Site statique, sans build ni dépendance : il suffit de déployer le dossier tel quel (Netlify, GitHub Pages…).

```
index.html            Page unique (header, hero, services, étapes, réseaux, CTA, footer)
assets/css/style.css  Styles (tokens de couleurs en haut du fichier, sections numérotées)
assets/js/main.js     Menu mobile, animations au scroll, effets au survol
assets/img/           Favicon
```

## Liens officiels
- WhatsApp : https://wa.me/213542522033
- Instagram : https://www.instagram.com/chakib_e.service/
- TikTok : https://www.tiktok.com/@chakib_e.service
- Facebook : https://www.facebook.com/eservice.chakib

## Modifier
- Couleurs : variables `--gold`, `--navy`, etc. dans `:root` (style.css).
- Messages WhatsApp pré-remplis : paramètre `?text=` de chaque lien `wa.me` dans index.html.

## Aperçu local
```bash
python3 -m http.server 8000
```
