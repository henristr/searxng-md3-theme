# searxng-md3-theme

`google-md3` ist ein neues CSS/LESS-Theme für SearXNGs `simple`-Templates (ohne Template-Änderungen), mit Google-ähnlicher Suche im MD3-Expressive-Stil.

## Verifizierte simple-Template Selektoren (aus `searxng/searxng`)

Quelle (master):
- `searx/templates/simple/search.html`
- `searx/templates/simple/results.html`
- `searx/templates/simple/macros.html`
- `searx/templates/simple/preferences.html`
- `searx/templates/simple/preferences/footer.html`

### Suchleiste
- Form: `form#search`
- Input: `input#q`
- Submit: `button#send_search`
- Clear: `button#clear_search`
- Wrapper: `#search_header`, `#search_view`, `.search_box`
- Autocomplete: `.autocomplete > ul`
- Filterzeile: `.search_filters`

### Ergebnis-Cards
- Container: `#results`, `#urls`
- Karte: `article.result` (zusätzlich `result-*`, `category-*`)
- URL-Kopf: `a.url_header`
- Favicon: `.favicon` (im URL-Kopf)
- URL-Text: `.url_wrapper`
- Titel: `h3`
- Content: `p.content`
- Meta/Engines: `.engines`

### Pagination
- Container: `nav#pagination`
- Vor/Zurück-Forms: `form.previous_page`, `form.next_page`
- Nummerierung: `.numbered_pagination`, `form.page_number`
- Aktuelle Seite: `input.page_number_current`

### Preferences
- Form: `form#search_form`
- Tabs: `.tabs`, `#tab-<id>`, `#tab-label-<id>`, `#tab-content-<id>`
- Feldgruppen: `fieldset`, `legend`, `.value`, `.description`
- Toggle: `.checkbox-onoff.reversed-checkbox`
- Footer-Aktionen: `.preferences_back a`

## LESS-Struktur

- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/tokens.less`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/base.less`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/header-searchbar.less`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/results.less`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/components.less`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/src/less/style.less`

Inhaltlich enthalten:
- MD3-Baseline-Tokens als CSS Custom Properties
- automatische Light/Dark-Umschaltung via `prefers-color-scheme`
- optionaler Hook: `[data-theme='light'|'dark']`
- separate Google-4-Farben-Akzentvariablen
- Roboto + Fallback-Stack
- pill-förmige Searchbar, MD3 State-Layer/Shadow-Übergänge
- Card-Result-Layout, Pagination, Preferences im einheitlichen Stil

## Build-Verifikation gegen echte SearXNG-Pipeline

Validiert mit echtem SearXNG-Build (aktuelle master-Version):

```bash
make node.env
make themes.simple
```

Die neuen LESS-Dateien wurden testweise in `client/simple/src/less/` eingebunden und erfolgreich durch `make themes.simple` gebaut.

## Fertige CSS-Dateien

- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/sxng-ltr.min.css`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/sxng-rtl.min.css`
- `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/searxng.css` (LTR-Kompatibilitätskopie)

## Welche Datei 1:1 in Docker kopieren/bind-mounten?

Wenn du wie beschrieben CSS im `simple`-Theme ersetzt:

- modern (aktuelle SearXNG simple-Templates): `sxng-ltr.min.css` (bzw. `sxng-rtl.min.css` für RTL)
- für deinen bestehenden Mount-Namen kannst du direkt diese Datei verwenden:
  - `/home/runner/work/searxng-md3-theme/searxng-md3-theme/google-md3/searxng.css`
