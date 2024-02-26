# Implementatiemodel IPDC-LPDC

Dit implementatiemodel is een implementatiemodel van
het [ICEG applicatieprofiel public service](https://belgif.github.io/thematic/models/public%20services/index_en.html)
en volgt het [OSLO Vocabularium 'Dienst'](https://data.vlaanderen.be/ns/dienst). Het wordt gebruikt om data
rond publieke dienstverlening uit te wisselen tussen IPDC (versie 3) en LPDC. Er wordt beschreven hoe er gecommuniceerd
kan worden vanuit en naar de
lokale producten- en dienstencatalogus (LPDC) en de interbestuurlijke producten- en dienstencatalogus (IPDC).

## Publicaties

- [Implementatiemodel](https://productencatalogus.data.vlaanderen.be/doc/implementatiemodel/ipdc-lpdc/)
    - [Gegegenereerde bestanden](https://github.com/Informatievlaanderen/data.vlaanderen.be-generated/tree/production/doc/implementatiemodel/ipdc-lpdc)
- [Vocabularium](https://productencatalogus.data.vlaanderen.be/ns/ipdc-lpdc/)
    - [Gegegenereerde bestanden](https://github.com/Informatievlaanderen/data.vlaanderen.be-generated/tree/production/ns/ipdc-lpdc)

## Werken met [Enterprise Architect](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF)

Extra metadata wordt aan het EA diargam toegevoegd in de vorm van tags. Deze tags hebben een beperkte lengte van 256
karakters. Om deze beperking te omzeilen is het mogelijk de tag waarde `NOTE` in te vullen en de echte waarde als note
toevoegen aan de tag. Een voorbeeld vind
je [hier](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF/blob/multilingual/Example.md). Een kort filmpje dat een
intro geeft hoe te werken met EA vind
je [hier](https://vlaamseoverheid.sharepoint.com/:v:/r/sites/informatie_vlaanderen/afdeling_informatiekanalen/MBPWP/PMBPWP_InformerenOpMaat/Enterprise%20Architect/Enterprise%20Architect%20uitlegske.mov?csf=1&web=1&e=JaXlmu).

### Package

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF?tab=readme-ov-file#package)
- `tags`:
    - `baseURI`: uri prefix voor alle niet extern gedefinieerde definities, zij krijgen de vorm `baseUri` + `name`
    - `baseURIabbrev`: voorkeur voor prefix afkorting

### Class, DataType, Enumeration

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF?tab=readme-ov-file#class-datatype--enumeration)

#### Class, DataType

- `name`: naam van de klasse
- `tags`
    - `uri`: in te vullen voor extern gedefinieerde klasses, heeft voorrang op default `baseURI``name` combinatie
    - `label-nl`: label
    - `definition-nl`: optionele beschrijving
    - `usageNote-nl`: optioneel gebruiksadvies

#### Enumeration

Enumerations worden enkel getoond als type van een attribuut op het applicatieprofiel/implementatiemodel. Ze worden niet
weergegeven in het vocabularium.
We modelleren alle codelijsten (`skos:ConceptScheme`) als enumeration klasses in Enterprise architect met volgende tags:

- `name`: naam van de enumeration
- `tags`
    - `uri`: `http://www.w3.org/2004/02/skos/core#Concept`
    - `label-nl`: label
    - `definition-nl`: beschrijving + owner
    - `usageNote-nl`: geldige waardes
    - `ap-codelist`: link naar de codelijst

### Attribuut

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF?tab=readme-ov-file#attribute)
- `naam`: naam van het attribuut
- `type`: type
  - One of the supported primitive XSD/RDF/RDFS types if the datatype is Boolean, Date, DateTime, Double,
      Duration,HTML, Int, Integer, LangString, Literal, Month, MonthDay, String, Time, URI, Year or YearMonth
  - The class (or datatype) whose name matches the datatype
- `multiplicity`: kardinaliteit 
- `tags`:
  - `uri`: in te vullen voor extern gedefinieerde klasses, heeft voorrang op default `baseURI` + `name` combinatie
  - `label-nl`: label
  - `definition-nl`: optionele beschrijving
  - `usageNote-nl`: optioneel gebruiksadvies

#### Enumeration

Een attribuut met als type een eigen enumeration modelleren we als volgt:

- `naam`: naam van het attribuut
- `type`: enumeration klasse
- `multiplicity`: kardinaliteit
- `tags`:
    - `uri`: specifiëren als een externe definitie gebruikt wordt
    - `label-nl`: label
    - `definition-nl`: beschrijving + owner
    - `usageNote-nl`: geldige waardes
    - `ap-codelist`: wordt overgenomen van enumeration

### Associations

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF?tab=readme-ov-file#connector)
- `name`: naam van de association
- `source`: bron
- `target`: doel
- `source multiplicity`: bron kardinaliteit (optioneel)
- `target multiplicity`: doel kardinaliteit
- `tags`
    - `uri`: in te vullen voor extern gedefinieerde associaties, heeft voorrang op default `baseURI``name` combinatie
    - `label-nl`: label
    - `definition-nl`: optionele beschrijving
    - `usageNote-nl`: optioneel gebruiksadvies
- A generalization connector will be converted into a `rdfs:subClassOf` triple

### Applicatieprofiel / Implementatiemodel tags

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF/blob/multilingual/OSLO-configuration.md#application-profile-terms)
- `ap-label-nl`
    - fallback: `label-nl`
- `ap-definition-nl`: beschrijving
    - fallback: `definition-nl`
- `ap-usageNote-nl`
    - fallback: `usageNote-nl`
- `ap-codelist`: url met verwijzing naar de codelijst

### Vocabularium tags

- [Documentatie](https://github.com/Informatievlaanderen/OSLO-EA-to-RDF/blob/multilingual/OSLO-configuration.md#core-vocabulary-terms)
- `equivalent`
- `uri`
- nl
    - `label-nl`
    - `definition-nl`
    - `usageNote-nl`
- en
    - `label-en`
    - `definition-en`
    - `usageNote-en`

## Editors

- Lees [deze richtlijnen](https://github.com/Informatievlaanderen/OSLO-toolchain/blob/master/doc-user/README.md)
    - [Branching strategie](https://github.com/Informatievlaanderen/OSLO-toolchain/blob/master/doc-user/thema-repo-versiecontrole.md)
- Allerlei [OSLO tooltjes](https://github.com/Informatievlaanderen/OSLO-allerleiTooltjes/blob/master/README.md)