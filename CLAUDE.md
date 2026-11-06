# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projektziel

Statische Unternehmenswebsite für **Alma AI Partners** (Domain: `alma-ai-partners.com`), eine AI- und Automatisierungsberatung für mittelständische Unternehmen. Zielgruppe sind Entscheider ohne tiefes KI-Wissen. Sprache der Seite: **Deutsch** (`lang="de"`), klare Sprache ohne Fachchinesisch.

## Dateistruktur

```
index.html        Startseite (Hero, Leistungen, Vorgehen, Über uns, Kontakt)
impressum.html    Gliederung + Platzhalter, KEIN fertiger Rechtstext
datenschutz.html  Gliederung + Platzhalter, KEIN fertiger Rechtstext
style.css         Gesamtes Styling (Design-Tokens als CSS-Variablen, Dark Mode via prefers-color-scheme)
script.js         Minimales JS (mobile Navigation); Seite muss auch ohne JS funktionieren
CLAUDE.md         Diese Datei
```

Mehrsprachigkeit: Deutsch liegt im Root, zusätzlich `en/index.html`, `pt/index.html`, `es/index.html`, `fr/index.html` (nur Startseiten, Pfade zu CSS/JS mit `../`). Sprachumschalter (`.lang-switch`) und `hreflang`-Links stehen in allen Seiten. Impressum und Datenschutz existieren nur auf Deutsch; die anderen Sprachen verlinken darauf mit Hinweis. Inhaltsänderungen an der Startseite müssen in allen fünf Sprachfassungen nachgezogen werden.

Header und Footer sind in allen HTML-Dateien dupliziert (kein Build, keine Includes). Änderungen an Navigation oder Footer müssen in allen drei Dateien nachgezogen werden.

## Befehle

Es gibt keinen Build, keine Tests und keinen Linter. Die Seite wird durch Öffnen von `index.html` im Browser angezeigt. Optional für einen lokalen Server: `python -m http.server 8000` im Projektordner.

## Regeln

- **Keine Build-Tools, keine Abhängigkeiten.** Nur `index.html`, `style.css`, `script.js` plus die zwei Rechtsseiten.
- **Keine externen Ressourcen:** keine Webfonts, CDNs, Skripte, Tracker, Analytics oder eingebetteten Dienste (Datenschutz). Es werden Systemschriften verwendet.
- **Nichts erfinden:** keine Referenzen, Kundennamen, Zahlen, Zitate, Teammitglieder oder Rechtstexte. Fehlende Inhalte als `[PLATZHALTER: ...]` kennzeichnen (genau diese Schreibweise, damit sie per Suche auffindbar sind: `grep -rn "PLATZHALTER" .`).
- **Rechtsseiten:** `impressum.html` und `datenschutz.html` enthalten nur Gliederung, Platzhalter und den Hinweis, dass die Inhalte rechtlich geprüft werden müssen. Keine eigenen Rechtsformulierungen ergänzen.
- **Kontakt** läuft ausschließlich über einen `mailto:`-Link (Adresse `gereon.wellmann@alma-ai-partners.com`; Postfach muss bei Google noch eingerichtet werden), kein Formular, kein Backend.
- **Barrierefreiheit:** ausreichende Kontraste (auch im Dark Mode), sichtbarer Fokus (`:focus-visible`), Skip-Link, semantisches HTML, Bedienung per Tastatur, `prefers-reduced-motion` respektieren.
- **Responsiv** bis Handy-Breite (ca. 360 px), Mobile-first-CSS.
- **Meta-Tags** (title, description, canonical, Open Graph) mit der Domain pflegen. Rechtsseiten tragen `noindex`, solange sie Platzhalter enthalten.
- Branch: `main`.
