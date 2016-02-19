#User_ -> Group_

##User from Group xy
https://intermediate.intra.politaktiv.org/linkeddata-liferay/page/User_/230092

###Join two mapped entities
map:User__group a d2rq:PropertyBridge;
	d2rq:belongsToClassMap map:User_;
	d2rq:property vocab:Group_ ;
	d2rq:refersToClassMap map:Group_ ;
	d2rq:join "User_.userId <= Users_Groups.userGroupId";
	d2rq:join "Users_Groups.userGroupId => Group_.groupId";
	.

##Group Blaubeuren
https://intermediate.intra.politaktiv.org/linkeddata-liferay/page/Group_/226376

##Joining Element
https://intermediate.intra.politaktiv.org/linkeddata-liferay/page/Users_Groups/226376/230092

##Query
SELECT DISTINCT * WHERE {
 ?user rdf:type vocab:User_ .
 ?user vocab:User__emailAddress ?email .
 ?user vocab:User__userId ?user_id .
 ?group rdf:type vocab:Group_ .
 ?group vocab:Group__friendlyURL ?group_url .
 ?group vocab:Group__groupId ?group_id .
 ?group vocab:Group__friendlyURL"/blaubeuren".
 ?user_group rdf:type vocab:Users_Groups .
 ?user_group vocab:Users_Groups_groupId ?group_id .
 ?user_group vocab:Users_Groups_userId ?user_id .
}
LIMIT 1000

