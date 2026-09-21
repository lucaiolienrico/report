# Fatture & Scontrini — Registro spese 🧾

App web **responsive** (PC e smartphone) per registrare **fatture** e **scontrini** tramite
**foto** (fotocamera dello smartphone) o **file PDF**, e consultare lo **storico**
organizzato nelle due sezioni dedicate.

- ✅ 100% statica: solo HTML/CSS/JS, **nessun server, nessun database esterno**
- ✅ Dati salvati **sul dispositivo** (IndexedDB del browser) — privacy totale
- ✅ Funziona **offline** dopo il primo caricamento (Service Worker + PWA)
- ✅ Pronta per **GitHub Pages**: fai push e l'app è online

---

## Funzionalità

| Area | Dettagli |
|---|---|
| 📄 Sezione **Fatture** | Storico fatture con foto/PDF allegati |
| 🧾 Sezione **Scontrini** | Storico scontrini con foto/PDF allegati |
| 📸 Registrazione | Scatto foto (fotocamera), upload immagine o PDF, drag & drop; compressione automatica delle foto |
| 📊 Panoramica | Totali, spesa del mese/anno, grafico ultimi 6 mesi, ultimi documenti |
| 🔍 Ricerca e filtri | Testo libero, categoria, mese, ordinamento (data, importo, fornitore) |
| ✏️ Gestione | Dettaglio con anteprima, modifica, download allegato, eliminazione |
| 💾 Backup | Export/Import JSON completo (allegati inclusi), export CSV per Excel |
| 📱 Responsive + PWA | Layout mobile-first con barra inferiore, installabile su smartphone |

## Struttura del progetto

```
.
├── index.html                  # L'APP COMPLETA (single-file: HTML+CSS+JS)
├── manifest.webmanifest        # Metadati PWA
├── sw.js                       # Service Worker (offline)
├── icon.svg / icon-*.png       # Icone
├── .nojekyll                   # Necessario per GitHub Pages
└── .github/workflows/deploy-pages.yml  # Deploy automatico su Pages
```

## Prova in locale

```bash
cd scontrini-fatture-app
python3 -m http.server 8000
# poi apri http://localhost:8000
```

(Oppure apri direttamente `index.html` nel browser — funziona anche da file.)

## Pubblicare su GitHub Pages (da PC o smartphone)

### Opzione A — da riga di comando

```bash
cd scontrini-fatture-app
git init
git add .
git commit -m "Fatture & Scontrini: prima versione"
git branch -M main
git remote add origin https://github.com/TUO-UTENTE/fatture-scontrini.git
git push -u origin main
```

Poi su GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
Il workflow incluso pubblica automaticamente a ogni push su `main`.

L'app sarà disponibile su:

```
https://TUO-UTENTE.github.io/fatture-scontrini/
```

### Opzione B — solo dal browser (anche da smartphone)

1. Crea un nuovo repository pubblico `fatture-scontrini` su github.com
2. Carica tutti i file di questa cartella (**Add file → Upload files**)
3. Vai in **Settings → Pages → Source: Deploy from a branch → Branch: main, / (root) → Save**
4. Dopo ~1 minuto l'app è online all'indirizzo qui sopra

### Installare l'app sullo smartphone

Apri l'URL di GitHub Pages da Chrome (Android) o Safari (iPhone) →
**"Aggiungi a schermata Home"**: si comporta come un'app nativa e funziona offline.

## Note tecniche

- **Storage:** IndexedDB (`fatture-scontrini-db`, store `documents`). Foto compresse a max 1920px JPEG.
- **Limiti:** allegati fino a 25 MB; lo spazio dipende dal browser/dispositivo.
- **Backup:** consigliato prima di cambiare browser/dispositivo (i dati vivono nel browser).
- **Browser supportati:** Chrome/Edge/Safari/Firefox recenti, desktop e mobile.
- **Privacy:** nessun dato lascia il dispositivo; nessuna dipendenza esterna/CDN.

## Licenza

MIT — libero uso personale e commerciale.
