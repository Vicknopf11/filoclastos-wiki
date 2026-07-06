---
title: Come funziona questa wiki
categoria: note
sommario: "Le convenzioni di base: come aggiungere pagine e collegarle."
---

Ogni pagina è un file Markdown dentro la cartella della sua categoria
(`note/`, `idee/`, `letture/`, `progetti/`). Il front matter in cima al
file decide dove compare:

```
---
title: Titolo della pagina
categoria: note
sommario: "Una riga che compare nell'elenco della categoria (opzionale)."
---
```

Per collegare una pagina a un'altra, usa un link Markdown relativo, per
esempio verso la pagina [idee](/idee/) o verso [un'idea specifica](/idee/esempio-idea/).

Per aggiungere una categoria nuova: crea una cartella, dentro un
`index.md` con `layout: categoria` e i campi `title`, `slug`,
`descrizione` — poi aggiungi la voce corrispondente in `_config.yml`
sotto `categorie`, così compare anche nella sidebar.
