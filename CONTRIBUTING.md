# Instalation des dépendances
Inutile pour l'instant car pas encore de dépendances

```
docker run \
  -v ${PWD}:/src \
  -v ${HOME}/hugo_cache:/tmp/hugo_cache \
  hugomods/hugo:exts \
  npm i
```

# Lancement local sur le port 8080
```
docker run -p 8080:8080 \
  -v ${PWD}:/src \
  -v ${HOME}/hugo_cache:/tmp/hugo_cache \
  hugomods/hugo:exts \
  hugo server --bind 0.0.0.0 -p 8080
```
