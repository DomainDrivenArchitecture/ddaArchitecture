##Find out users for site with friendly url "/blaubeuren"

SELECT DISTINCT * WHERE {
 ?user rdf:type vocab:User_ .
 ?user vocab:User__emailAddress ?email .
 ?user_group rdf:type vocab:Users_Groups .
 ?group rdf:type vocab:Group_ .
 ?group vocab:Group__friendlyURL ?group_url .
 ?group vocab:Group__friendlyURL"/blaubeuren".
 ?user_group vocab:Users_Groups_groupId ?group_id .
 ?user_group vocab:Users_Groups_userId ?user_id .
 ?user vocab:User__userId ?user_id .
 ?group vocab:Group__groupId ?group_id .
}
LIMIT 1000

##Find out Assets for WebContents (not working yet).

SELECT DISTINCT * WHERE {
 ?asset rdf:type vocab:AssetEntry .
 ?journal rdf:type vocab:JournalArticle .
 ?journal vocab:JournalArticle_id_ ?journalId .
 ?asset vocab:AssetEntry_classPK ?journalId .
}
LIMIT 100


##Join two mapped entities
map:User__group a d2rq:PropertyBridge;
	d2rq:belongsToClassMap map:User_;
	d2rq:property vocab:Group_ ;
	d2rq:refersToClassMap map:Group_ ;
	d2rq:join "User_.userId <= Users_UserGroups.userGroupId";
	d2rq:join "Users_UserGroups.userGroupId => Group_.groupId";