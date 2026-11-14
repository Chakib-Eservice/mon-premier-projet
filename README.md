# Chakib E-Service — site web

Site vitrine de **Chakib E-Service** (Constantine) : services administratifs et numériques.

Site statique en **un seul fichier** : `index.html` contient le HTML, le CSS (balise `<style>`), le JavaScript (balise `<script>`) et le favicon.
Aucun fichier externe à oublier : le design s'affiche même si on ouvre `index.html` directement ou si on ne déploie que ce fichier (Netlify, GitHub Pages…).

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
