# Requirements Linked Data für PolitAktiv
Ziel: 
Aus Beiträgen von Bürgern werden standardisierte Aussagen extrahiert und dabei in beide Richtungen navigierbar verlinkt. Die standardisierten Aussagen sind von den Moderatoren vorgegeben. 

## Basic
* Ressourcen / Ontologien sind eindeutig referenziert
* Ressourcen / Ontologien sind per Webtechnik dereferenzierbar
  * für Menschen
  * für WebService Clients
* SPARQL Abfragen über Ontologien und Ressourcen 
  
## Authorisierung auf Mandantenebene
* Authentifizierung
* Autorisierung für Mandanten

## Bearbeiten
* Ontologie erstellen
* Ontologie bearbeiten & erweitern
* Instanzen erstellen
* Instanzen bearbeiten & erweitern

## Verlinkung
* Verlinkungsregeln definieren & erweitern
* Verlinkung automatisiert als Verlinkungs-Vorschlag erstellen
* Verlinkungs-Vorschläge mit manueller Verlinkung zusammenführen.
* Verlinkungs-Vorschläge können von manuellen Verlinkungen entmischt werden.

### Idea: Multi-Source Ability
* Establish a multi-source ability by deploying .war-files into a servlet container (e.g. tomcat), running on a server
* use a distinct .war-file for every business application
* thus, databases that do not belong together stay separated
* when accessing the the server, the client application can be accessed by the URL which contains the name of the .war-file
* thus, the URLs define namespaces for different business applications
