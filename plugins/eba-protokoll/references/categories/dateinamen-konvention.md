# EBA-Dateinamen-Konvention für Protokolle

EBA-Protokolle folgen einer projektübergreifenden Dateinamenskonvention. Der
Name wird zunächst als **Dateibasis ohne Endung** gebildet. Der Renderer hängt
anschließend ausschließlich die Endung des festgelegten QMG-Ausgabeformats an:

- Word-Ursprung: dieselbe Dateibasis als `.docx` und `.pdf`.
- Excel-Ursprung (BIM oder ausdrücklich gewählte Excel-Variante): `.xlsx`.
- Fortschreibung: zusätzlich `protokoll-state.json`.

Eine `.md`-Datei ist niemals ein fertiges Protokoll. Sie darf nur als
temporärer interner Renderer-Eingang existieren und wird nach erfolgreicher
Ausgabe gelöscht.

## Grundschema der Dateibasis

```
<PrjNr>-<PrjKZ>-<FirmaKZ>[-<Bereich>]-<Typ>-<JJMMTT>[-<Suffix>]
```

| Feld | Beschreibung | Beispiele |
|------|--------------|-----------|
| `<PrjNr>` | EBA-Projektnummer (3-stellig) | `553`, `549`, `541` |
| `<PrjKZ>` | Projekt-Kurzname (Großbuchstaben) | `WIL`, `VTS`, `MAR` |
| `<FirmaKZ>` | Firma-Kürzel des Erstellers (in der Regel `EBA`) | `EBA` |
| `<Bereich>` | optionaler fachlicher Schwerpunkt | `BIM`, `TWP`, `BL` |
| `<Typ>` | Typ-Kürzel des Protokolls | `PK`, `PLB-PK`, `JF` |
| `<JJMMTT>` | Datum 2-stellig: Jahr, Monat, Tag | `260324` für 24.03.2026 |
| `<Suffix>` | optional, z.B. geprüft/KI-erstellt oder Version | `g-KI`, `v2`, `Entwurf` |

## Typ-Kürzel und Ausgabeformat

| Kürzel | Format | Finale Datei(en) |
|--------|--------|------------------|
| `GN` | Gesprächsnotiz (`gespraechsnotiz`) | DOCX + PDF |
| `PK` | Generelles Protokoll | DOCX + PDF |
| `PLB-PK` | Planungsbesprechung (`protokoll-lp1-4`) | DOCX + PDF |
| `BIM-PK-JF-NN` | BIM-Koordinations-Jour-Fixe Nr. NN | XLSX |
| `BL-PK` | Bauleitung (`protokoll-lp5`) | DOCX + PDF |
| `WS-PK` | Workshop (`protokoll-einfach`) | DOCX + PDF |

## Beispiele

```
553-WIL-EBA-PLB-PK-260324.docx
553-WIL-EBA-PLB-PK-260324.pdf
553-WIL-EBA_BIM-PK-JF-07_260331-g-KI.xlsx
549-VTS-EBA-PK-240112.docx
549-VTS-EBA-PK-240112.pdf
541-MAR-EBA-BL-PK-260415.docx
541-MAR-EBA-BL-PK-260415.pdf
```

## Mapping zur Plugin-Skill

| Plugin-Skill | Default-Typ-Kürzel im Dateinamen |
|--------------|----------------------------------|
| `gespraechsnotiz` | `GN` |
| `protokoll-einfach` | `WS-PK` |
| `protokoll-lp1-4` | `PLB-PK` |
| `protokoll-lp1-4` (BIM-Variante) | `BIM-PK-JF-NN` |
| `protokoll-lp5` | `BL-PK` |

## Vereinfachte Dateibasis

Wenn der Nutzer keine EBA-Dateinamenskonvention verlangt, verwendet das Plugin:

```
<JJJJ-MM-TT>_<projekt-kurzname>_<typ>
```

Beispiele der finalen Dateien:

```
2026-03-24_WIL_planungsbesprechung-11.docx
2026-03-24_WIL_planungsbesprechung-11.pdf
2026-03-31_WIL_bim-jf-07.xlsx
```

Beide Namensschemata sind gültig. Das EBA-Schema ist die offizielle Konvention
für abgelegte Dokumente; das vereinfachte Schema ist der Plugin-Default.

## Verzeichnisstruktur

```
protokolle/
└── 553-WIL/
    ├── 553-WIL-EBA-PLB-PK-260224.docx
    ├── 553-WIL-EBA-PLB-PK-260224.pdf
    ├── 553-WIL-EBA-PLB-PK-260324.docx
    ├── 553-WIL-EBA-PLB-PK-260324.pdf
    ├── 553-WIL-EBA_BIM-PK-JF-07_260331.xlsx
    └── protokoll-state.json
```

Wenn der Nutzer „Speichere als EBA-Dateiname“ oder „use EBA filename“ sagt,
bildet das Plugin die offizielle Dateibasis. Die Endung wird nie aus dem
Zwischenformat übernommen, sondern folgt immer dem gewählten QMG-Format.
