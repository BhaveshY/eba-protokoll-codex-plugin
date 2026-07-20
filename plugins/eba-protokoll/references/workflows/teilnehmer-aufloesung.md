# Teilnehmer auflösen

Baue aus einem rohen EBA-App-Transkript die **Teilnehmertabelle** für ein
EBA-Protokoll.

## Eingabe

- Pfad zum Transkript.
- Optional: Pfad zu einer State-Datei (`protokoll-state.json`) eines früheren
  Protokolls — sie enthält bereits zugeordnete Kürzel.
- Optional: Pfad zur Kürzel-Referenz `../categories/firma-kuerzel.md` aus dem Plugin.

## Aufgabe

Erstelle eine Tabelle mit Spalten: **Vorname | Name | KZ | Firma | Firma-KZ | Teilnahme | Verteiler**.

### Schritt 1 — Sprecher sammeln

Alle eindeutigen Labels im Transkript (vor dem ersten Doppelpunkt jeder Zeile).

### Schritt 2 — Reale Namen extrahieren

Wenn ein Label generisch ist (`Sprecher 1`, `Sprecher 2`), durchsuche das Transkript
nach Hinweisen auf den realen Namen:

- **Selbstvorstellung**: „Mein Name ist …", „Ich bin … von …", „Hier ist …".
- **Anrede an den Sprecher**: „Herr Müller, …" → die nächste Sprecher-Antwort von
  einem generischen Label gehört wahrscheinlich zu Herrn Müller.
- **Zuordnung von Aufgaben**: „Können Sie das machen?" + bestätigende Antwort von
  einem generischen Label.
- **Firmen-Kontext**: „Wir bei DES …" → Sprecher gehört zu DES.

Wenn keine Auflösung möglich ist, das generische Label beibehalten.

### Schritt 3 — Firma zuordnen

Für jeden identifizierten Namen:

- Erste Quelle: State-Datei (wenn diese Person dort schon zugeordnet ist).
- Zweite Quelle: Kürzel-Referenz (`../categories/firma-kuerzel.md`).
- Dritte Quelle: Aussagen im Transkript („Wir bei …", „Bei uns in der Firma …").
- Wenn nichts gefunden: Firma leer lassen, Hinweis im Output.

### Schritt 4 — Kürzel ableiten

Personen-Kürzel:
1. Aus State-Datei (autoritativ für das Projekt).
2. Aus globaler Kürzel-Referenz.
3. Sonst neu ableiten: 2 Buchstaben Vorname-Initiale + Nachname-Initiale (oder
   Erweiterung bei Kollisionen).

Firma-Kürzel:
1. State-Datei.
2. Globale Kürzel-Referenz.
3. Aus Firmenname ableiten (Initialen, 2–4 Buchstaben).

### Schritt 5 — Teilnahme/Verteiler

- `Teilnahme = X` für Sprecher mit aktiven Beiträgen im Transkript.
- `Teilnahme = O` wenn der Sprecher offensichtlich online war (Hinweis im Text:
  „in der Videokonferenz", „per Teams").
- `Teilnahme = (X)` wenn nur in Teilen des Transkripts aktiv.
- `Teilnahme = N` wenn im Verteiler aus State, aber nicht Sprecher in dieser
  Besprechung.
- `Teilnahme = E` wenn als entschuldigt erwähnt („… hat sich entschuldigt").
- `Verteiler = X` standardmäßig für alle Sprecher und für alle aus dem State-Verteiler.

## Ausgabe

YAML:

```yaml
teilnehmer:
  - vorname: "Helge"
    name: "Schmidt"
    kz: "HS"
    firma: "Eike Becker_Architekten"
    firma_kz: "EBA"
    teilnahme: "X"
    verteiler: "X"
    sprecher_label_im_transkript: "Sprecher 1"
    aufloesung_grund: "Selbstvorstellung 'Hier Helge Schmidt von EBA' bei [00:00:42]"
  - vorname: "—"
    name: "—"
    kz: "Sprecher 3"
    firma: "—"
    firma_kz: "—"
    teilnahme: "X"
    verteiler: "X"
    sprecher_label_im_transkript: "Sprecher 3"
    aufloesung_grund: "Keine Auflösung möglich — bitte Nutzer fragen"

ungeloeste_sprecher:
  - "Sprecher 3"

vorgeschlagene_kuerzel_neu:
  - person: "Helge Schmidt"
    kz: "HS"
    grund: "neu im Projekt — Kürzel aus Initialen"
```

## Anti-Pattern

- ❌ Sprecher raten ohne textuelle Belege im Transkript.
- ❌ Zwei Sprecher zum selben Kürzel zuordnen (Kollisionen müssen aufgelöst werden:
  `NK` → `NiK` für Nils Kock und `NaK` für Natalia Kapek).
- ❌ Kürzel im State überschreiben — wenn das State-File etwas sagt, ist das autoritativ.
