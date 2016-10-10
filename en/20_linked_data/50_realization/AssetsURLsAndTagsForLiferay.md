# Content -> Url & -> Category
Zeige den Asset eines Webcontents an, dazu einen Titel, dazu die URL zum Webcontent, dazu die neueste Version (falls keine Veränderung zur vorherigen stattgefunden hat, dazu das Schlagwort das assoziiert ist, dazu den Autor (der Webcontent in Liferay gefasst hat), dazu den Inhalt

Dinge die manuell zu verändern sind:
im letzten BIND: der Servername
die friendlyURL des aktuellen Diskussionskreises


Ergebnis der Query/Anmerkungen:
Die Query kann so wie sie ist kopiert, eingefügt und ausgeführt werden.
Es wird auffallen: Webcontents sind mehrmals erhalten, das liegt daran, dass es mehrere Versionen von Webcontents gibt. Hier könnte man vielleicht mit einer intelligenten Filterung/Gruppierung immer nur die neueste Version herausbekommen; das bleibt noch zu tun. 
Der Link zum Webcontent wird mit String-Operationen erstellt. Diese sind allgemein gehalten und könnten für besonders seltsamen Input Ergebnisse liefern, die einen nicht-funktionierenden Link liefern. Das liegt in der Natur der Sache; die meisten Links sollten allerdings funktionieren.
Beachte: Es gibt mehrere Ansichten im Asset-Publisher. Manchmal sind alle Einträge einzeln ansehbar (z.B. Blaubeuren), manchmal hängen viele Einträge zusammen (z.B. Uhingen). In letzterem Fall führt der Link auf die richtige Seite, den Entrag selbst muss man aber selbst suchen, da er nicht referenzierbar ist.




!!!!!!!!!!!!!!!!!!!!!--------------------------!!!!!!!!!!!!!!!!!!!!!

			    Fehlerbehandlung!

Es handelt sich um eine aufwändige Rechenoperation! Unter Umständen beschwert sich der Server mit folgender Fehlermeldung:

Request Entity Too Large
The requested resource
/linkeddata-liferay/snorql/
does not allow request data with GET requests, or the amount of data provided in the request exceeds the capacity limit.
Apache Server at intermediate.intra.politaktiv.org Port 443

Wenn das passiert habe ich zwei Möglichkeiten gefunden, den Fehler zu umgehen:
1. "Reset"-Button drücken und neu Query neu einfügen
2. Eine Zeile aus der Query löschen; dann die Query ausführen (sollte problemlos laufen); dann die Zeile wieder einfügen, dann sollte die Query auch wieder laufen

Fehler bleibt zu analysieren

!!!!!!!!!!!!!!!!!!!!!--------------------------!!!!!!!!!!!!!!!!!!!!!


SELECT DISTINCT ?assetOfWebcontent ?titel ?url max(?version) ?DK ?Schlagwort ?autor ?webcontentInhalt WHERE {

  #Suche den Asset zu einem Webcontent, verlinke sie
  ?webcontent vocab:JournalArticle_resourcePrimKey ?webcontentAssetLink .
  ?assetOfWebcontent vocab:AssetEntry_classPK ?webcontentAssetLink .

  #die Id des Assets
  ?assetOfWebcontent vocab:AssetEntry_entryId ?entryId .

  #Stelle Verbindung zwischen Asset und AssetTag (=Schlagwort) her
  ?entriesTagLink vocab:AssetEntries_AssetTags_entryId ?entryId .
  ?entriesTagLink vocab:AssetEntries_AssetTags_tagId ?tagId .

  # die Id des Tags
  ?tag vocab:AssetTag_tagId ?tagId .


  #Extrahiere aus dem Webcontent: Schlagwort, Titel, Version, Inhalt, Autor
  #der Titel wird hierbei aus dem HTML-Gewusel, das ihn umgibt, herausgeschnitten
  ?tag vocab:AssetTag_name ?Schlagwort .
  ?webcontent vocab:JournalArticle_content ?webcontentInhalt .
  ?webcontent vocab:JournalArticle_userName ?autor .
  ?webcontent vocab:JournalArticle_version ?version .
  ?webcontent vocab:JournalArticle_urlTitle ?webcontentURLTitle .
  ?webcontent vocab:JournalArticle_title ?webcontentTitel.
  BIND (replace(strbefore(?webcontentTitel, "</Title>"), "<.*>", "") AS ?titel) .

  # Schränke Suche auf Diskussionskreis ein, z.B. Blaubeuren
  ?webcontent vocab:JournalArticle_groupId ?groupId .
  ?community vocab:Group__friendlyURL "/blaubeuren" .
  ?community vocab:Group__friendlyURL ?DK .
  ?community vocab:Group__groupId ?groupId .

  # Suche url der Page/Seite (in der Datenbank: Layout), auf der Asset liegt
  ?asset vocab:AssetEntry_layoutUuid ?uuid .
  ?layout vocab:Layout_uuid_ ?uuid .
  ?layout vocab:Layout_friendlyURL ?layoutURL .
  ?layout vocab:Layout_groupId ?groupId .

  # Schränke Suche ein auf Pages/Seiten, welche in ihren TypeSettings das Portlet 101 (Nummer des Asset Publishers) einbinden
  ?layout vocab:Layout_typeSettings ?typeSettings .
  FILTER regex(?typeSettings, "101_INSTANCE_*") 

  # Suche die die Portlet-Id des Asset Publishers, welcher einen Content einbindet
  # bringe dazu die Typesettings in eine künstliche Struktur, um mit dem nächsten Aufruf den richtigen Substring errechnen zu können
  BIND (replace(replace(replace(?typeSettings, "\n", "#"), " ", "#"), ",", "#") AS ?searchString) .
  # berechne die Id aus dem Substring
  BIND (strbefore (strafter(?searchString, "101_INSTANCE_"), "#") AS ?assetPublisherInstanceId) .
  # erstelle Link (Beispiellink: https://intermediate.intra.politaktiv.org/web/blaubeuren/pinnwand/-/asset_publisher/3Xv2Pv6noxxQ/content/ernst-georg-bayer-or-pappelau-katastrophale-zustande-)
  BIND ((concat ("intermediate.intra.politaktiv.org/web", ?DK, ?layoutURL, "/-/asset_publisher/", ?assetPublisherInstanceId, "/content/", ?webcontentURLTitle)) AS ?url) .


} 
GROUP BY ?assetOfWebcontent ?titel ?url ?DK ?Schlagwort ?autor ?webcontentInhalt
ORDER BY DESC(?url)





##Query
'''
﻿SELECT DISTINCT ?assetOfWebcontent ?titel ?url max(?version) ?DK ?Schlagwort ?autor ?webcontentInhalt WHERE { 

  #Get the asset, a webcontent belongs to
  ?webcontent vocab:AssetEntryOfJournalArticle ?assetOfWebcontent .

  #Get the asset tags that belong to an asset
  ?assetOfWebcontent vocab:AssetTagOfAssetEntry ?tag .

  #Extrahiere from the webcontent: asset tag name, title, version, content, author
  ?tag vocab:AssetTag_name ?Schlagwort .
  ?webcontent vocab:JournalArticle_content ?webcontentInhalt .
  ?webcontent vocab:JournalArticle_userName ?autor .
  ?webcontent vocab:JournalArticle_version ?version .
  ?webcontent vocab:JournalArticle_urlTitle ?webcontentURLTitle .
  ?webcontent vocab:JournalArticle_title ?webcontentTitel.
  #remove HTML-tags from title
  BIND (replace(strbefore(?webcontentTitel, "</Title>"), "<.*>", "") AS ?titel) .

  # limit to one community (Diskussionskreis) (e.g. Blaubeuren)
  ?webcontent vocab:JournalArticle_groupId ?groupId .
  ?community vocab:Group__friendlyURL "/blaubeuren" .
  ?community vocab:Group__friendlyURL ?DK .
  ?community vocab:Group__groupId ?groupId .

  # URL
  # get layout (=page) that is linked to the asset
  ?asset vocab:LayoutOfAssetEntry ?layout .
  ?layout vocab:Layout_friendlyURL ?layoutURL .
  ?layout vocab:Layout_groupId ?groupId .

  # limit to pages that mention portlet 101 (portlet number of the asset publisher) in their type settings
  ?layout vocab:Layout_typeSettings ?typeSettings .
  FILTER regex(?typeSettings, "101_INSTANCE_*") 

  # search portlet-id of that specific asset publisher that include the webcontent
  # therefore, create an artificial string ...
  BIND (replace(replace(replace(?typeSettings, "\n", "#"), " ", "#"), ",", "#") AS ?searchString) .
  # ... that can be used for further string operations (that extract the portlet id)
  BIND (strbefore (strafter(?searchString, "101_INSTANCE_"), "#") AS ?assetPublisherInstanceId) .
  # create Link (e.g. https://politaktiv.org/web/blaubeuren/pinnwand/-/asset_publisher/3Xv2Pv6noxxQ/content/ernst-georg-bayer-or-pappelau-katastrophale-zustande-)
  BIND ((concat ("intermediate.intra.politaktiv.org/web", ?DK, ?layoutURL, "/-/asset_publisher/", ?assetPublisherInstanceId, "/content/", ?webcontentURLTitle)) AS ?url) .

} 
GROUP BY ?assetOfWebcontent ?titel ?url ?DK ?Schlagwort ?autor ?webcontentInhalt
ORDER BY DESC(?url)
'''

## Explanation
Erklärung der Datenbank dahinter:
Für den Webcontent gilt: Jede Version, die von ihm existierte, existiert auch in der Datenbank. Aus dem Webcontent lassen sich leicht Informationen über den Titel, die Version, den DK (über die Gruppe), den Autor und den Inhalt herausfinden.
Schwieriger für: die verknüften Schlagwörter (werden zur Kategorisierung verwendet), sowie eine direkte URL zum Webcontent:

Schlagwörter:
Ein Webcontent ist ein Asset, deshalb muss diese Verbindung hergestellt werden, denn Schlagwörter sind dem Asset zugeordnet, nicht dem Webcontent. 
Link:
Der Link besteht aus mehreren Teilstücken. Es muss herausgefunden, wo der Asset-Publisher liegt, der den Link anzeigt, damit der Link direkt angezeigt werden kann.
Zum einen muss herausgefunden werden, in welchem Unterpfad des DKs sich dieser Asset-Publisher befindet; dies geschieht über das Layout (ein Layout Eintrag entspricht einer Webpage im Browser). In den Settings eines Layouts stehen die eingebunden Portlets. Es muss also nach dem AssetPublisher in den Layouts gesucht werden. Hat man den Asset-Publisher, so kann man vom dazugehörigen Layout auslesen, wie der Subpfad zu diesem lautet. Des Weiteren wird für die URL die ID des Asset-Publishers benötigt. Ihn kann man kompliziert aus den Settings herausschneiden. Außerdem benötigt man noch den Titel des Webcontents, dieser steckt wieder trivial im Webcontent.