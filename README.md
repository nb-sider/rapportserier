# Rapportserier – NB innleveringsoppfølging

Dashboard for å overvåke om norske rapportserier er avlevert til Nasjonalbiblioteket.

## GitHub Pages-oppsett (gratis)

### 1. Opprett GitHub-repo

1. Gå til [github.com/new](https://github.com/new)
2. Gi repoet et navn, f.eks. `nb-rapportserier`
3. Sett det til **Public** (GitHub Pages krever dette på gratis plan)
4. Klikk **Create repository**

### 2. Last opp filene

Last opp disse filene til repoet:
- `index.html`
- `serier.json`
- `sjekk_cache.json` *(forhåndslagrede sjekk-resultater – valgfri, men anbefalt)*

Det enkleste er via GitHub-webgrensesnittet: klikk **Add file → Upload files**.

### 3. Aktiver GitHub Pages

1. Gå til **Settings → Pages** i repoet
2. Under **Source**: velg **Deploy from a branch**
3. Velg branch **main** og mappe **/ (root)**
4. Klikk **Save**

Etter 1–2 minutter er dashboardet tilgjengelig på:
`https://[ditt-brukernavn].github.io/[repo-navn]/`

---

## Oppdatere serielisten

Når du legger til eller endrer serier i `rapportserier_konfig.xlsx`:

```bash
python3 generer_serier_json.py
```

Last deretter opp den nye `serier.json` til GitHub-repoet.

---

## Lokal versjon (med utvidet funksjonalitet)

For å kjøre den lokale versjonen med Python-server (støtter scraping av utgivers nettside i tillegg til NVA):

```bash
python3 dashboard_server.py
```

Åpnes automatisk på http://localhost:8765

---

## Tekniske detaljer

**GitHub Pages-versjon (`index.html`):**
- Kaller NB-katalog API og NVA API direkte fra nettleseren
- Resultater lagres i nettleserens localStorage (vedvarer mellom besøk)
- Kun NVA-basert mangel-sjekk (ingen scraping av utgivers nettside)

**Lokal versjon (`dashboard.html` + `dashboard_server.py`):**
- Støtter i tillegg scraping av utgivers nettside
- Persistent cache i `rapportserier_cache.json`
