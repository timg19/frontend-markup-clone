## Navigation
- [Was ist XPath](#was-ist-xpath)
- [Datenmodell und Knotentypen](#datenmodell-und-knotentypen)
- [Pfad-Syntax und Startpunkte](#pfad-syntax-und-startpunkte)
- [Achsen](#achsen)
- [Filter](#filter)
- [Funktionen und Operatoren](#funktionen-und-operatoren)
- [Namespaces (TEI) – wichtig!](#namespaces-tei--wichtig)
- [Beispiele für TEI-Selektoren](#beispiele-für-tei-selektoren)
- [Existenzprüfung](#existenzprüfung)

---

## Was ist XPath
- Sprache zur Adressierung/Selektion von Teilen eines XML-Baums/einer XML-Datei.
- Wird in XSLT, XQuery, XProc, Schematron u. a. verwendet.
- Versionen: XPath 1.0 (breit unterstützt), 2.0/3.1 (reichere Typen, Funktionen, Sequenzen; in Python nicht standardmäßig verfügbar).

## Datenmodell und Knotentypen
- Knotenarten: Element, Attribut, Text, Dokument-Knoten, Namespace, Kommentar, Processing Instruction.
- Kontext bestimmt Auswertung, z. B.:
  - aktueller Knoten: `.`

## Pfad-Syntax und Startpunkte
- `/` Wurzel
- `.` aktueller Knoten
- `..` Elternknoten des aktuellen Knotens
- `//` alle Nachfahren unterhalb (inkl. aktueller Knoten)
- Kindschritte: `a/b/c`, beliebige Nachfahren: `a//c`
- Attribute: `@id`, `//@xml:id`

Beispiele:
- `/tei:TEI/tei:text/tei:body/tei:div`
- `//tei:p`
- `.//tei:note`

## Achsen
- `child::tei:p` → Kind-Elemente (Abkürzung: `tei:p`)
- `descendant::tei:note` → Nachfahren (Abkürzung: `//tei:note`)
- `parent::node()` → Elternknoten (Abkürzung: `..`)
- `ancestor::tei:div` → Vorfahren
- `following-sibling::tei:p` / `preceding-sibling::tei:p` → Geschwister
- `attribute::xml:id` → Attribute (Abkürzung: `@xml:id`)
- `self::node()` → aktueller Knoten

## Filter
- Prädikate in eckigen Klammern filtern Node-Sets/Sequenzen.
- Nach Wert: `tei:div[@type='letter']`
- Nach Position:
  - `tei:div[1]` (erstes `div`-Kind)
  - `(//tei:note)[1]` (erste Note im Dokument)
- Kombination mit `and`: `tei:div[@type='letter' and @n=3]`
- Positionen: `position()`, `last()`
  - `tei:pb[position()=1]` (erste Seitenmarke)
  - `tei:pb[last()]` (letzte Seitenmarke)

## Funktionen und Operatoren
- Zeichenketten: `string()`, `normalize-space()`, `contains()`, `starts-with()`, `substring()`
- Numerisch: `count()`, `sum()`, `number()`
- Boolesch: `boolean()`, `not()`, `true() / false()`, `exists()` (2.0+)
- Sequenzen (2.0+): `distinct-values()`, FLWOR (`for $x in … return …`), `string-join()`
- Operatoren: `=`, `!=`, `<`, `<=`, `>`, `>=`; logische `and`, `or`
- Beispiele:
  - `contains(., 'Renner')`
  - `normalize-space(tei:head) != '')`

## Namespaces (TEI) – wichtig!
- TEI-Elemente stehen im Namespace `http://www.tei-c.org/ns/1.0` und müssen im XPath mit Präfix angesprochen werden.
- Im XSLT-Stylesheet z. B.:
  - `xmlns:tei="http://www.tei-c.org/ns/1.0"`
  - Selektoren: `//tei:div`, `/tei:TEI/tei:teiHeader`
- Attribute wie `@xml:id` sind im `xml`-Namespace: `@xml:id` funktioniert in XSLT ohne zusätzliche Präfix-Deklaration.

## Beispiele für TEI-Selektoren
- Alle Absätze: `//tei:p`
- Erste Überschrift im body: `(/tei:TEI/tei:text/tei:body//tei:head)[1]`
- Personen mit `@ref`: `//tei:persName[@ref]`
- Noten in Apparaten: `//tei:note[@type='app']`
- Briefe vom Typ „letter“ mit Nummer: `//tei:div[@type='letter' and @n]`