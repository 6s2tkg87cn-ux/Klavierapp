# Tastenfall auf der Schul-Homepage einbinden

## 1. Dateien hochladen

Diese Dateien gehören zusammen und müssen im **selben Ordner** auf dem Schul-Server liegen:

```
tastenfall/
├── index.html
└── fonts/
    ├── unbounded.woff2
    ├── lexend.woff2
    ├── OFL-Unbounded.txt
    └── OFL-Lexend.txt
```

Die App lädt nichts von fremden Servern: keine Google-Schriften, kein Tracking, keine Cookies.
Sie braucht keine Datenbank und kein PHP, nur einen ganz normalen Webspace.

**Wichtig:** Die Seite muss über `https://` erreichbar sein. Sonst sperren die Browser das Mikrofon.

## 2. In eine Seite einbinden

Viele Schul-Systeme (z. B. WordPress, Joomla, IServ, Moodle) erlauben keine eigenen
HTML-Dateien mit JavaScript in einer Seite. Dann bindet man die App als Fenster (`iframe`) ein:

```html
<iframe
  src="https://www.meine-schule.de/tastenfall/index.html"
  title="Tastenfall – Klavier lernen"
  allow="microphone; fullscreen; midi; autoplay"
  allowfullscreen
  style="width:100%; height:80vh; min-height:560px; border:0; border-radius:12px;">
</iframe>
<p><a href="https://www.meine-schule.de/tastenfall/index.html" target="_blank" rel="noopener">Tastenfall im eigenen Fenster öffnen</a></p>
```

Die Adresse in `src` und im Link durch die echte Adresse ersetzen.

- `allow="microphone"` ist nötig, damit „Mikrofon“ (Spielen am echten Klavier) im Fenster funktioniert.
- `midi` erlaubt ein Keyboard am Kabel (Chrome, Edge).
- Ist die App eingebettet, zeigt sie oben den Knopf **„In neuem Fenster öffnen“**.
  Im eigenen Fenster klappen Mikrofon und Vollbild immer, auch wenn das Schul-System
  die `allow`-Angaben entfernt.

Liegt die App auf einer anderen Adresse als die Schul-Homepage (z. B. GitHub Pages), funktioniert
das `iframe` genauso. Für den Datenschutz ist es aber am einfachsten, wenn alles auf dem Schul-Server liegt.

## 3. Für Datenschutz und Barrierefreiheit

Was die App macht und was nicht – für die Datenschutzerklärung der Schule:

- **Mikrofon:** Nur nach Klick auf „Mikrofon“ und Erlaubnis im Browser. Der Ton wird nur im
  Browser ausgewertet, um gespielte Töne zu erkennen. Nichts wird aufgenommen, gespeichert oder verschickt.
- **Gespeichert** wird nur im Browser des Geräts (`localStorage`): die Sterne pro Lied,
  ob das Metronom an ist und ob die Hilfe schon gezeigt wurde. Keine Cookies, keine Konten, keine Namen.
- **Eigene MIDI-Dateien** werden nur auf dem Gerät geöffnet und nicht hochgeladen.
- **Keine externen Dienste:** Schriften liegen im Ordner `fonts/`, es gibt kein Tracking und keine Werbung.

Barrierefreiheit: Die Bedienelemente sind mit Tastatur bedienbar und für Bildschirmleser beschriftet.
Das Spielfeld mit den fallenden Noten ist eine grafische Übung und kann nicht barrierefrei sein.
Das kann in der Erklärung zur Barrierefreiheit der Schule als Einschränkung genannt werden.

## Lizenzen

- Alle eingebauten Lieder sind gemeinfrei (Volkslieder bzw. Komponisten seit über 70 Jahren verstorben).
- Schriften: Unbounded und Lexend, SIL Open Font License 1.1 (siehe `fonts/OFL-*.txt`).
