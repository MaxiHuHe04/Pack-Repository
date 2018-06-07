# Datapack-Index

## Manifeste:
Hier werden die einzelnen MC-Addon-Typen deklariert
### Typen:
    - datapack
    - mcfunction
    - structure

### manifest.json
    enthält informationen über den index-aufbau
    - manifest-version: zu Verwendende Version zum Parsen des Schemas
    - datapacks: Liste von Datapack-Indizes
    - mcfunctions: Liste von MCFunction-Indizes
    - structures: Liste von Struktur-Indizes

### \<typ\>_external.json
    enthält informationen über extern verfügbare Addons, die nicht vom BasicPack-Team gehostet werden
    - manifest-version: zu Verwendende Version zum Parsen des Schemas
    - external: Array von externen typenspezifischen Addons
        Für Jedes Element:
        - String-Identifier muss der festgelegten id entsprechen
        - Unterelemente:
            - String-Identifier entspricht einer festgelegten Version
            - url: direkter download des Addons
            - changelog: [optional] Änderungsprotokoll für diese Version des Addons
            - dependencies: [optional] Enthält Abhängigkeiten des Addons.
                unterstützte Typen: "required", "incompatible", typen als Listen mit Einträgen im Format id@versionRange, siehe "https://dev.to/ebud7/maven-version-ranges" (versionRange optional)

## Index-Objektstruktur
    - manifest-version: zu Verwendende Version zum Parsen des Schemas
    - objects: Array von Spezifischen Addons
        - Addon:
            - id: spezifische ID des addons, einzigartig für den jeweiligen Addon-Typ. Format: [groupID:artifactID], siehe "https://maven.apache.org/ref/3.5.3/maven-model/maven.html"
            - name: [optional] Anzeigename des packs, muss nicht einzigartig sein und darf Kleinbuchstaben, Großbuchstaben, Ziffern, Leerzeichen, Bindestriche und Understriche enthalten.
            - url: [optional] Webseite des Addons
            - versions: Liste aus spezifischen Versions-Strings
            - download: Download-Typ des Addons (zulässig für manifest-version 1.0.0: external, maven)
                - external: in <typ>_external.json datei definiert.
                - maven: in einem Maven Repository gehostet, url definiert in "maven"-Sektion
            - maven: nur benötigt, wenn Download-Typ = maven; URL des Maven Repositorys
            - versions: Liste von verfügbaren Versionen des Addons (Strings)
