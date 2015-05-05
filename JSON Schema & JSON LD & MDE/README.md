## Intro
Thema ist Daten und ihre Metadaten. Zusammengefasst:
* [JSON](http://json.org/) ist ein neutrales Datenformat / Notationsformat, hauptsächlich für Maschinen und Serialisation.
* [YAML](http://yaml.org/) ist ein Superset von JSON, mehr Features, angenehmer zu schreiben
* Es kann Daten oder Metadaten beinhalten.
  * Daten:
    * Datenstruktur
    * Daten-Inhalt
  * Metadatenformate:
    * JSON Schema kann die Datenstruktur beschreiben ("type")
    * JSON Schema bringt auch eine sehr einfache Semantik mit sich ("format") z.B. Email, URL um die Dateninhalte zu beschreiben.
    * JSON LD ist darauf spezialisiert komplexe Semantik zu erfassen (auch Zusammenhänge). 

-----------------------
 
## JSON Schema
> JSON Schema beschreibt die Struktur von JSON Dokumenten und JavaScript Objekten. Es ist sehr simpel und aktuell ein IETF draft. Die Spezifikation von JSON Schema ist in JSON Schema geschrieben, es kann sich also selbst beschreiben.

### Beispiel
```json
{
    "title": "Example Schema",
    "type": "object",
    "properties": {
        "firstName": {
            "type": "string"
        },
        "lastName": {
            "type": "string"
        },
        "age": {
            "description": "Age in years",
            "type": "integer",
            "minimum": 0
        }
    },
    "required": ["firstName", "lastName"]
}
```

### Use cases
* Validation
* Spezifikation (m2m)
* Dokumentation generieren
* Zufallsdaten generieren
* UI / Formulare / Systeme generieren (-> MDE)
 
### Links
* [JSON Schema](http://json-schema.org/)
* [JSON Schema JS Bin](http://jsbin.com/fanuti/21/edit?js)
* [JSON Schema Tutorial](http://spacetelescope.github.io/understanding-json-schema/)
* [Beispiel: plastic.js](http://plasticjs.org/) -> [Code Example](https://github.com/Fannon/plastic.js/blob/master/src/modules/display/AdvancedTable.js)
* [mobo](https://www.npmjs.com/package/mobo) -> Mobo Viewer (live-demo)
 
--------------------------

## JSON-LD
> JSON-LD kann Fakten und Sachverhalte maschineninterpretierbar beschreiben und die Semantik dahinter beschreiben. Kommt aus der Semantic Web Szene, ist allerdings deutlich pragmatischer orientiert. 

### Beispiel 
> Beschreibt eine [schema.org/Person](http://schema.org/Person)

```json
{
  "@context": "http://schema.org/",
  "@type": "Person",
  "name": "Jane Doe",
  "jobTitle": "Professor",
  "telephone": "(425) 123-4567",
  "url": "http://www.janedoe.com"
}
```

### Use Cases
* Annotation für Webseiten, hauptsächlich SEO / maschineninterpretierbarkeit (schema.org!)
* Annotation von Datenquellen, helfen bei Automatisierung der Auswertung / Zusammenfügen 
* APIs, als Austauschformat, aber auch um Domain-Konzepte (Ontologien) zwischen Maschinen auszutauschen. (m2m, AI)
* Ontologien sind hilfreich um sich auf ein gemeinsames Vokabular zu einigen. Sie sind sowohl für Menschen als auch Maschinen hilfreich um eindeutig Aussagen treffen zu können. 

### Links
* [JSON LD](http://json-ld.org/)
* [Schema.org](http://schema.org/)

-----------------------

## MDE
> Model Driven Engineering bezeichnet die Entwicklung von (domänenspezifischen) Modellen. Ein Modell ist eine vereinfachte, reduzierte Version der Wirklichkeit.

### Hintergrund
* Viele Begriffe: MDE, MDD, MDA
* Großer Hype, vor allem unter UML (De facto Standard für MDE).
* Wurde dann tot-spezifiziert (UML hat 850+ Seiten Spezifikation) und sehr komplex (MDA, meta-meta-modelle)
* Heute hauptsächlich in Enterprise Bereich zu finden, da die Code-Qualität sehr hoch und konsistent sein kann. Im WebDev Bereich kaum bekannt.

### Konzepte
* Hauptziel: Abstraktion, bis hin dazu "domain specific languages (DSL)" bzw. "modeling / specification languages" zu schaffen, die das fertige System auf hoher Abstraktionsebene kompakt beschreiben.
* Oft kann aus dem Modell (dass in einer DSL geschrieben wurde) automatisiert generiert werden:
  * Dokumentation
  * Endsystem:
    * Interfaces
    * Systemkomponenten
    * Komplette Systeme inkl. Code
  * Tests
* Kann Entwicklung agiler machen, da weniger Code geschrieben werden muss
* Ändert sich das Zielsystem oder bestimme Anforderungen muss im Idealfall nur der Generator angepasst werden und nicht das Modell
* Daten (und ihre Strukturen) leben oft länger als die Systeme die sie generieren / verwenden!

### Use Cases
* APIs 
* CMS und KMS Systeme
* Datenbankmodelle, inkl. CRUD

### Links
* [Beispiel - Swagger.io](http://editor.swagger.io/#/)
* [mobo](https://www.npmjs.com/package/mobo) -> [Project Example](https://github.com/Fannon/mobo/tree/master/examples/hardware-yaml)