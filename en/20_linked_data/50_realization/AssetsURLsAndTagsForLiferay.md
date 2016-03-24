# Content -> Url & -> Category
SELECT DISTINCT ?assetOfWebcontent ?titel ?url max(?version) ?DK ?Schlagwort ?autor ?webcontentInhalt WHERE { 

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

## Query
SELECT DISTINCT * WHERE {

 ?journal rdf:type vocab:JournalArticle .
 ?journal vocab:JournalArticle_title ?title .
 ?journal vocab:JournalArticle_content ?content .
 ?journal vocab:JournalArticle_groupId ?groupId .
 
 ?group rdf:type vocab:Group_ .
 ?group vocab:Group__friendlyURL ?group_url .
 ?group vocab:Group__friendlyURL"/blaubeuren".
 ?group vocab:Group__groupId ?groupId . 

}
LIMIT 1000


