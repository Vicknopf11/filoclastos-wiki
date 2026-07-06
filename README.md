# Quaderno (wiki personale)

Wiki personale con pagine Jekyll collegate tra loro. Stesso motore
(Jekyll) del resto del cluster Filoclastos, ma con un registro visivo
diverso e più intimo — non fa parte delle "testate" pubbliche, anche se
pubblicamente raggiungibile. Solo tu puoi modificarne il contenuto
(vedi "Pubblicazione" più sotto).

## Struttura

```
index.md              — home, elenco delle categorie
note/                  — categoria "Note", con index.md + pagine
idee/                  — categoria "Idee"
letture/               — categoria "Letture"
progetti/              — categoria "Progetti"
_layouts/default.html  — sidebar + area contenuto
_layouts/pagina.html   — layout di default per ogni pagina di contenuto
_layouts/categoria.html — layout per gli index.md di categoria (elenco automatico)
_includes/sidebar.html — sidebar con ricerca e categorie
assets/css/main.css    — stile (registro "quaderno", diverso dalla "gazzetta" del resto del cluster)
search.json            — indice generato automaticamente per la ricerca lato client
```

### Aggiungere una pagina

Crea un file `.md` dentro la cartella della categoria giusta, con questo
front matter:

```
---
title: Titolo della pagina
categoria: note
sommario: "Una riga opzionale, compare nell'elenco della categoria."
---

Contenuto in Markdown. Per collegare un'altra pagina:
[testo del link](/idee/esempio-idea/)
```

Compare automaticamente nell'elenco della sua categoria — non serve
aggiornare nient'altro.

### Aggiungere una categoria nuova

1. Crea una cartella, con dentro un `index.md`:
   ```
   ---
   layout: categoria
   title: Nome Categoria
   slug: nome-categoria
   descrizione: "Una riga di descrizione."
   ---
   ```
2. Aggiungi la voce corrispondente in `_config.yml` sotto `categorie:`,
   così compare anche nella sidebar.

## Pubblicazione

Chi ha accesso in scrittura è deciso da GitHub, non dal sito: solo tu
puoi modificare il repository, a meno che tu non inviti esplicitamente
qualcun altro come collaboratore (Settings → Collaborators). Il fatto
che il sito sia pubblico non cambia questo — pubblico qui significa
"chiunque abbia il link può leggere", non "chiunque può scrivere".

1. Crea il repository su GitHub come **Public**.
2. Push normale:

   ```bash
   cd filoclastos-wiki
   git init
   git add .
   git commit -m "Struttura iniziale della wiki"
   git branch -M main
   git remote add origin https://github.com/Vicknopf11/filoclastos-wiki.git
   git push -u origin main
   ```

3. Su GitHub: **Settings → Pages** → Source: `Deploy from a branch`,
   branch `main`, cartella `/ (root)` → Save. Poi, sotto **Custom
   domain**, inserisci `wiki.filoclastos.it` e salva (il file `CNAME` è
   già nel repository). Spunta **Enforce HTTPS** una volta che il DNS è
   verificato.

## DNS su Aruba

```
CNAME   wiki   vicknopf11.github.io
```

## Nota sull'indicizzazione

Il layout include `<meta name="robots" content="noindex, nofollow">` su
ogni pagina: il sito è raggiungibile da chiunque abbia il link diretto,
ma Google e gli altri motori di ricerca non lo indicizzeranno. Se in
futuro vuoi che compaia nei risultati di ricerca, rimuovi quella riga da
`_layouts/default.html`.
