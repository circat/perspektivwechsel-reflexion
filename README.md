# Perspektivwechsel

Eine statische, datensparsame Selbstreflexions-App zu antisemitischen Deutungs- und Handlungsmustern. Sie ist bewusst als **erste psychoedukative App**, nicht als validierter Persönlichkeitstest oder Risikoinstrument konzipiert.

## Was die App leistet

- 20 Aussagen, vier pro Bereich, mit fünfstufiger Zustimmungsskala
- lokale Auswertung im Browser: keine Konten, Cookies, Analyse- oder Cloud-APIs
- Score von 1–125 plus transparente Teilwerte
- wertschätzende Auswertung und Links zu RIAS und OFEK
- Tastaturbedienung, sichtbare Fokuszustände, semantische Formulare und responsive Darstellung

## Fachliche Grundlage und Grenzen

Die fünf Bereiche beziehen sich auf Gordon Allports Beschreibung von Vorurteilsmanifestationen (Sprache, Vermeidung, Diskriminierung, physischer Angriff, Vernichtung) aus *The Nature of Prejudice* (1954). Das Modell dient hier zur pädagogischen Strukturierung; es ist **keine kausale Stufenfolge** und sagt bei Einzelpersonen keine zukünftige Handlung voraus.

Die Aussagen wurden an der nicht rechtsverbindlichen [IHRA-Arbeitsdefinition](https://holocaustremembrance.com/resources/working-definition-antisemitism) orientiert. Sie behandeln Verschwörungsmythen, Kollektivschuld, Holocaustrelativierung, Diskriminierung und Gewaltlegitimation. Die App trennt ausdrücklich Kritik an konkreter israelischer Regierungspolitik von antisemitischen Kollektivzuschreibungen.

Der Score ist eine nachvollziehbare **Reflexionshilfe**, keine klinische, forensische oder psychometrisch validierte Messung. Er darf nicht für Personalentscheidungen, Zugangskontrollen, Forschungsergebnisse oder die Beurteilung Dritter eingesetzt werden. Für einen wissenschaftlich validierten Test wären unter anderem Item-Entwicklung mit Betroffenenperspektiven, kognitive Interviews, repräsentative Stichproben, Reliabilitäts- und Validitätsanalysen sowie eine unabhängige Ethikprüfung nötig.

Für Betroffene oder Zeug:innen antisemitischer Vorfälle verlinkt die App auf [RIAS](https://report-antisemitism.de/) und [OFEK](https://ofek-beratung.de/). OFEK bietet in Deutschland professionelle, vertrauliche und mehrsprachige Beratung.

## Berechnung

Jede Antwort hat einen Wert von 1 (stimme überhaupt nicht zu) bis 5 (stimme voll zu). Je Bereich werden vier Antworten summiert und gewichtet:

| Bereich | Gewicht |
| --- | ---: |
| Sprache | 1,0 |
| Distanzierung | 1,2 |
| Diskriminierung | 1,5 |
| Gewaltakzeptanz | 2,0 |
| Entmenschlichung | 2,5 |

Der gewichtete Rohwert wird linear auf 1–125 normiert. Niedrige Werte zeigen die Zurückweisung der abgefragten Aussagen; höhere Werte markieren Gesprächs- und Lernbedarf. Sie bezeichnen keine Person und stellen keine Gefahrprognose dar.

## Lokal starten

Keine Installation nötig. `index.html` im Browser öffnen oder einen statischen Server nutzen:

```powershell
python -m http.server 8080
```

Dann `http://localhost:8080` öffnen.

## Cloudflare Pages Deployment

1. Bei Cloudflare ein Pages-Projekt anlegen und dieses GitHub-Repository verbinden.
2. Als Produktionsbranch `master` wählen.
3. Build command leer lassen; Build output directory ist `.`.
4. Alternativ nach `wrangler login` direkt deployen:

```powershell
npx wrangler pages deploy . --project-name perspektivwechsel-reflexion
```

Die Datei `_headers` setzt Sicherheitsheader. Da die Anwendung statisch ist, ist kein Server oder Geheimnis nötig.

## Projektstruktur

| Datei | Zweck |
| --- | --- |
| `index.html` | Struktur und zugängliche UI |
| `styles.css` | responsives Design, Tacho und Druckansicht |
| `app.js` | Fragenkatalog, Navigation und lokale Berechnung |
| `_headers` | Cloudflare-Sicherheitsheader |
| `wrangler.toml` | Cloudflare-Konfiguration |

## Quellen

- Gordon W. Allport (1954): *The Nature of Prejudice*.
- [IHRA: Working definition of antisemitism](https://holocaustremembrance.com/resources/working-definition-antisemitism).
- [National Academies: Measuring Racial Discrimination](https://www.nationalacademies.org/read/10887/chapter/7) – Einordnung von Allports Stufen und ihrer gesellschaftlichen Bedingungen.
- [RIAS Bundesverband](https://report-antisemitism.de/), [OFEK e.V.](https://ofek-beratung.de/).
