# CLAUDE CODE PROMPTS — IMPORTIA LEGAL DOCS INTEGRATION

> **Hinweis Jay:** Dieser Prompt ist in zwei Phasen aufgeteilt. Erst Phase 1 (Analyse) ausführen, Antwort bewerten, dann Phase 2 (Implementation) starten. Niemals beide Phasen auf einmal abfeuern, sonst macht Claude Code Annahmen, die du nicht kontrollieren kannst.

---

## PHASE 1 — ANALYSE & VORSCHLAG

```
Du bist ein erfahrener Senior Frontend Developer mit Spezialisierung auf statische Websites, SEO und DSGVO-konforme Web-Implementierung. Du arbeitest am Importia Projekt, einem Handelshaus für Import, Export und Handel mit Sitz in Düren, Deutschland.

KONTEXT
========

Das Repository enthält die aktuelle Visitenkartenseite von Importia, derzeit deployed auf importia.pages.dev (Cloudflare Pages). Die Site ist aktuell nur eine Hauptseite ohne Legal Docs Subpages. Es müssen drei rechtskonforme Legal Doc Subpages eingebaut werden, plus zwei Vorhalt-Dokumente, die ins Repo gehören aber NICHT verlinkt werden.

Im Repo Root liegen folgende Markdown-Dateien bereit, die ich manuell hineingelegt habe:

LIVE-DOKUMENTE (müssen als Subpages live geschaltet werden):
1. IMPRESSUM.md
2. DATENSCHUTZ.md
3. COOKIE_HINWEIS.md (interne Beratungsempfehlung, NICHT live, nur ablegen in /legal/_internal/)

VORHALT-DOKUMENTE (nur ins Repo legen, nicht verlinken, nicht als Subpage):
4. VORHALT_AGB_B2B.md
5. VORHALT_AGB_B2C.md
6. VORHALT_WIDERRUFSBELEHRUNG.md

DEINE AUFGABE — PHASE 1 (NUR ANALYSE)
======================================

In dieser Phase implementierst du noch NICHTS. Du analysierst nur und lieferst einen Vorschlag.

Führe folgende Schritte aus:

1. STRUKTUR-SCAN
   - Liste die komplette Verzeichnisstruktur des Repos auf (max. 3 Ebenen tief)
   - Identifiziere die Tech-Stack: Vanilla HTML/CSS/JS, Astro, Next.js, Vite, oder etwas anderes
   - Identifiziere wo CSS/Styling lebt (inline, CSS Datei, Tailwind, CSS-in-JS, etc)
   - Identifiziere wo der Footer-Bereich der Hauptseite ist (HTML-Element, Komponente, etc)
   - Identifiziere wie Routing funktioniert (file-based, routes config, sonstiges)

2. DESIGN-SYSTEM EXTRAHIEREN
   - Welche Schriftarten verwendet die Site? (Font Family, Gewichte)
   - Welche Farbpalette? (Hex Codes der Primärfarben, Hintergrund, Text)
   - Welche Spacing/Layout-Konventionen? (max-width, padding, margins)
   - Welcher Schreibstil/Tonalität? (Beobachtung aus dem aktuellen Copy)
   - Gibt es einen erkennbaren typografischen Charakter? (z.B. Klassisch, Editorial, Tech, Handelshaus-Stil)

3. IMPLEMENTATION-VORSCHLAG
   Auf Basis deiner Analyse, schlage VOR (noch nicht ausführen):
   
   a) URL-Struktur: Wie sollen die Subpages erreichbar sein?
      Beispiel: /impressum, /datenschutz oder /legal/impressum, /legal/datenschutz
      Empfehlung welche Variante besser ist und warum
   
   b) Datei-Organisation: Wo werden die HTML-Files (oder Astro/Next-Pages) abgelegt?
      Wo werden die Markdown-Quelldateien archiviert?
      Wo landen die Vorhalt-Dokumente (mein Vorschlag: /legal/_internal/, mit Hinweis-README dass diese nicht live sind)
   
   c) Footer-Integration: Wie genau wird der Footer der Hauptseite erweitert?
      Konkret: Welcher Code-Block muss wie verändert werden, um zwei dezente Links auf Impressum und Datenschutz hinzuzufügen?
      Das Design der Footer-Links muss sich nahtlos in das bestehende minimalistische Design einfügen
   
   d) Subpage-Layout: Sollen die Legal Docs Subpages dasselbe Layout/Header/Footer wie die Hauptseite haben oder ein reduziertes Lese-Layout?
      Empfehlung: Konsistenz mit Hauptseite (gleicher Header, gleicher Footer), aber mit fokussiertem Lese-Container für die Legal-Inhalte
   
   e) Markdown-zu-HTML-Konvertierung: Wie konvertierst du die .md Dateien in die finalen Pages?
      Falls Vanilla HTML: Manuell konvertieren mit semantischer Struktur
      Falls Astro/Next.js: Welche Markdown-Plugins/Loader nutzen
   
   f) SEO/Meta:
      - <title>-Tags pro Subpage
      - <meta name="description"> pro Subpage  
      - <meta name="robots"> Empfehlung (index,follow vs. noindex für Legal Docs)
      - canonical Tags
      - hreflang nur falls mehrsprachig (aktuell nur Deutsch)
   
   g) Sitemap & robots.txt: Müssen diese aktualisiert werden? Falls ja, wie?

WICHTIGE EINSCHRÄNKUNGEN
=========================

- Du implementierst in dieser Phase NICHTS, weder Files erstellen noch editieren
- Du gibst keine kompletten Code-Files aus, nur strukturelle Vorschläge
- Du fragst NICHT nach mehr Kontext, du analysierst was im Repo ist
- Du gehst NICHT davon aus dass eine bestimmte Tech vorliegt, du prüfst es

OUTPUT-FORMAT
=============

Strukturiere deine Antwort exakt wie folgt:

# 1. STRUKTUR-SCAN
[Verzeichnisbaum, Tech-Stack-Identifikation, Findings]

# 2. DESIGN-SYSTEM
[Schriften, Farben, Layout-Konventionen, Tonalität]

# 3. IMPLEMENTATION-VORSCHLAG
## 3a) URL-Struktur
## 3b) Datei-Organisation
## 3c) Footer-Integration (mit konkretem Code-Diff-Vorschlag)
## 3d) Subpage-Layout
## 3e) Markdown-Konvertierung
## 3f) SEO/Meta
## 3g) Sitemap & robots.txt

# 4. RISIKEN & EDGE-CASES
[Was könnte schief gehen, worauf muss geachtet werden]

# 5. FREIGABE-FRAGE AN MICH
[Welche konkreten Entscheidungen brauchst du von mir, bevor du in Phase 2 implementierst]

Beginne jetzt mit der Analyse.
```

---

## PHASE 2 — IMPLEMENTATION (NACH FREIGABE VON PHASE 1)

> **Wichtig:** Diesen Phase 2 Prompt erst absenden, NACHDEM du Phase 1 reviewt und ggf. Anpassungen vorgenommen hast. Falls Claude Code in Phase 1 sinnvolle Empfehlungen gemacht hat, kannst du den unten stehenden Prompt 1:1 nutzen. Falls Claude Code etwas Unerwartetes vorgeschlagen hat, passe den Prompt entsprechend an.

```
Sehr gut, dein Vorschlag aus Phase 1 ist freigegeben mit folgenden Anpassungen:

[FALLS KEINE ANPASSUNGEN NÖTIG: Schreibe hier "Keine Anpassungen, setze deinen Vorschlag aus Phase 1 unverändert um."]

[FALLS ANPASSUNGEN NÖTIG: Liste sie hier konkret auf, z.B.:
- URL-Struktur soll /impressum sein, nicht /legal/impressum
- Footer-Links sollen rechtsbündig erscheinen
- etc.]

DEINE AUFGABE — PHASE 2 (VOLLSTÄNDIGE IMPLEMENTATION)
======================================================

Setze jetzt die Integration vollständig um. Halte dich an folgende Regeln:

1. KOMPLETTE FILE-REPLACEMENTS
   - Wenn du eine bestehende Datei änderst (z.B. index.html für den Footer), gib die KOMPLETTE neue Datei aus, nicht nur den geänderten Bereich
   - Keine "..." Auslassungen, keine Diff-Syntax
   - Ich kopiere die Files 1:1 in das Repo, also müssen sie produktionsfertig sein
   - Hintergrund: Ich arbeite ausschließlich über copy-paste, nicht über manuelle Edits

2. NEUE FILES VOLLSTÄNDIG
   - Jede neue Datei (z.B. impressum.html) als kompletten, lauffähigen Inhalt ausgeben
   - Inkl. <!DOCTYPE html>, vollständigem <head>, semantischem <body>, etc.

3. MARKDOWN-KONVERTIERUNG SAUBER
   - Lies die Markdown-Inhalte aus IMPRESSUM.md und DATENSCHUTZ.md
   - Konvertiere zu semantischem HTML mit:
     - <h1> für den Hauptkopf
     - <h2> für Hauptabschnitte (## in Markdown)
     - <h3> für Unterabschnitte (### in Markdown)
     - <p> für Absätze
     - <ul>/<ol> für Listen
     - <strong> für Fettungen
   - Fettgedruckte Großbuchstaben-Blöcke (z.B. WIDERSPRUCHSRECHT-Klausel in der Datenschutzerklärung) als <strong> rendern, NICHT als CSS text-transform, sodass Screen Reader das korrekt vorlesen

4. STYLING DER SUBPAGES
   - Konsistent zum Hauptseiten-Design
   - Lese-Container max-width zwischen 680px und 760px für optimale Zeilenlänge (50-75 Zeichen pro Zeile)
   - Großzügige line-height (1.6 bis 1.7)
   - Klare Hierarchie zwischen H1/H2/H3 mit ausreichenden vertikalen Abständen
   - Mobile-first responsiv
   - Keine externen Schriftarten nachladen, falls die Hauptseite es nicht tut (sonst DSGVO-Problem)

5. FOOTER-INTEGRATION
   - Zwei dezente Links: "Impressum" und "Datenschutz"
   - Nahtlose Integration in das bestehende Footer-Design
   - Auf Mobile gleichermaßen erreichbar
   - Keine Aufblähung des bestehenden Footers, kein Re-Design des Gesamtfooters

6. VORHALT-DOKUMENTE
   - Erstelle einen Ordner /legal/_internal/ (oder vergleichbar)
   - Lege die drei Vorhalt-Markdowns dorthin (VORHALT_AGB_B2B.md, VORHALT_AGB_B2C.md, VORHALT_WIDERRUFSBELEHRUNG.md)
   - Lege ebenfalls COOKIE_HINWEIS.md dorthin (ist eine interne Beratungsempfehlung, kein Live-Dokument)
   - Erstelle ein README.md in diesem Ordner mit dem Inhalt:
     ```
     # Interne Legal Docs (nicht live)
     
     Dieser Ordner enthält Vorhalt-Dokumente und interne Beratungs-Memos. Diese Dateien sind NICHT auf der Live-Site verlinkt und werden NICHT öffentlich ausgeliefert.
     
     Inhalt:
     - VORHALT_AGB_B2B.md — AGB-Template für künftiges B2B-Geschäft
     - VORHALT_AGB_B2C.md — AGB-Template für künftiges B2C-Geschäft  
     - VORHALT_WIDERRUFSBELEHRUNG.md — Widerrufsbelehrung-Template für künftiges B2C-Geschäft
     - COOKIE_HINWEIS.md — Interne Beratungsempfehlung zum Thema Cookie-Banner
     
     Vor produktivem Einsatz dieser Dokumente ist eine fachanwaltliche Schlussprüfung erforderlich.
     ```

7. SICHERSTELLEN DASS VORHALT-FILES NICHT AUSGELIEFERT WERDEN
   - Falls die Tech-Stack es erlaubt (z.B. Astro, Next.js mit page exclusion), die _internal/ Pages aus dem Build ausschließen
   - Falls Vanilla HTML mit Cloudflare Pages: Eine .gitignore reicht hier nicht, da .md Files generell nicht von Cloudflare Pages als Pages ausgeliefert werden, aber zur Sicherheit in /functions oder via _redirects/_headers eine 404-Regel für /_internal/* hinzufügen, oder den Ordner mit "_" prefix verwenden, der von Cloudflare Pages als private gilt

8. SEO/META PRO SUBPAGE
   - <title>: "Impressum — Importia" bzw. "Datenschutzerklärung — Importia"
   - <meta name="description">: Kurzer Satz pro Page (max 155 Zeichen)
   - <meta name="robots" content="index,follow"> für Impressum und Datenschutz (Suchmaschinen sollen sie finden, ist Best Practice)
   - canonical Tag pro Subpage

9. ROBOTS.TXT & SITEMAP.XML
   - Falls keine vorhanden: erstellen
   - sitemap.xml mit allen drei URLs (/, /impressum, /datenschutz)
   - robots.txt mit allow für root, disallow für /_internal/ oder vergleichbar

10. NACH IMPLEMENTATION
    - Liste mir alle erstellten und veränderten Files auf
    - Gib mir eine konkrete Anweisung, was ich als Mensch testen muss bevor ich pushe (z.B. "öffne /impressum in einem Inkognito-Browser und prüfe auf Layout-Brüche")
    - Erinnere mich daran, dass die drei Platzhalter im Impressum (Telefonnummer, USt-IdNr, Bildnachweise) noch vom Mandanten ausgefüllt werden müssen

WICHTIGE EINSCHRÄNKUNGEN
=========================

- Keine externen JavaScript-Bibliotheken hinzufügen, falls die Site keine nutzt
- Keine Tracking-Scripts, keine Analytics, keine Drittanbieter
- Keine Inline-Styles wo CSS-Klassen sinnvoller wären
- Keine ungetesteten Annahmen — falls etwas nicht eindeutig ist, frage NACH Implementation in einem Hinweis-Block am Ende, NICHT vorher

Beginne mit der Implementation. Liefere die Files in der Reihenfolge:
1. impressum.html
2. datenschutz.html
3. Geänderte index.html (mit Footer-Update)
4. Eventuell geänderte CSS-Datei (falls separate CSS existiert)
5. /legal/_internal/ Ordner Inhalt
6. sitemap.xml
7. robots.txt (falls relevant)
8. Abschluss-Report mit Test-Checklist

Los.
```

---

## NUTZUNGSHINWEIS

**Workflow:**

1. Phase 1 Prompt copy-pasten in Claude Code
2. Antwort von Claude Code lesen, prüfen ob Vorschlag passt
3. Falls ja: Phase 2 Prompt mit "Keine Anpassungen" senden
4. Falls Anpassungen: Phase 2 Prompt mit konkreten Anpassungen senden
5. Implementation testen (Test-Checklist von Claude Code befolgen)
6. Erst dann pushen / deployen

**Falls Claude Code in Phase 1 etwas Unerwartetes findet:**
- Tech-Stack ist nicht das was du erwartet hast: Kein Problem, der Phase 2 Prompt ist Tech-agnostisch geschrieben
- Repo ist leer oder broken: Stop, prüfe zuerst manuell ob du im richtigen Repo bist

**Token-Schonung:**
Falls die Antwort von Phase 1 sehr lang ist und du nicht alles einzeln durchgehen willst, kannst du in Phase 2 schreiben: "Setze deinen Vorschlag aus Phase 1 vollständig um, ich vertraue deiner Analyse." Das funktioniert in 80% der Fälle, in den restlichen 20% musst du einzelne Punkte korrigieren. Bei Legal Docs würde ich aber empfehlen, mindestens die URL-Struktur und das Footer-Design selbst zu reviewen.
