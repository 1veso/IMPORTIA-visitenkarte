# Legal Docs Quellordner

Dieser Ordner enthält die Markdown-Quelldateien für die Legal Docs der Importia UG (haftungsbeschränkt).

## Live-Dokumente (werden als HTML-Subpages auf der Site gerendert)

- `IMPRESSUM.md` → `/impressum.html`
- `DATENSCHUTZ.md` → `/datenschutz.html`

Die HTML-Subpages liegen im Repo-Root und werden bei jedem Cloudflare-Pages-Deploy mit ausgeliefert. Inhaltliche Änderungen an den Markdown-Quellen werden NICHT automatisch in die HTML-Files übernommen — nach jeder Änderung an `IMPRESSUM.md` oder `DATENSCHUTZ.md` muss der Inhalt der jeweiligen `*.html` im Root manuell synchronisiert werden.

## Interne Dokumente (NICHT live, nur intern)

- `COOKIE_HINWEIS.md` — Beratungsempfehlung zum Thema Cookie-Banner
- `VORHALT_AGB_B2B.md` — AGB-Template für künftiges B2B-Geschäft
- `VORHALT_AGB_B2C.md` — AGB-Template für künftiges B2C-Geschäft
- `VORHALT_WIDERRUFSBELEHRUNG.md` — Widerrufsbelehrung-Template für künftiges B2C-Geschäft

Diese Dokumente sind über `robots.txt` von der Indexierung ausgeschlossen und werden NICHT als Subpages auf der Live-Site verlinkt. Sie dienen als Vorhalt für späteren Bedarf.

Vor produktivem Einsatz der Vorhalt-Dokumente ist eine fachanwaltliche Schlussprüfung erforderlich.

## Hinweis zu Prompt-Dokumenten

Der ursprüngliche Prompt `CLAUDE_CODE_PROMPT_LEGAL_DOCS.md` lag in einer früheren Iteration in diesem Ordner. Er wurde aus Gründen der öffentlichen Erreichbarkeit nach `_legal_docs/` (Underscore-Prefix) verschoben — Cloudflare Pages ignoriert Ordner mit `_`-Prefix beim Build, sodass der Prompt nicht öffentlich abrufbar ist.

## Offene Platzhalter in den Live-Dokumenten

Die folgenden Stellen in `IMPRESSUM.md` und `DATENSCHUTZ.md` müssen vom Mandanten gefüllt werden, sobald die Daten vorliegen. Die Aktualisierung muss in BEIDEN Dateien erfolgen (Markdown-Quelle UND HTML-Subpage im Repo-Root):

- Telefonnummer: `+49 (0) [Telefonnummer einsetzen]` — Pflichtangabe nach § 5 DDG
- USt-IdNr.: `DE [USt-IdNr. einsetzen, …]` — sobald vom Bundeszentralamt für Steuern erteilt
- Bildnachweise (Impressum) — falls eigenes oder lizenziertes Bildmaterial verwendet wird
