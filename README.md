# spring-data-elasticsearch

To run this application, Please follow the following instructions.
1. Download Elastic Search zip file from https://www.elastic.co/downloads/elasticsearch and put it in any location of your pc and extract it.
Note: you have to match spring-boot-version, spring-data-elasticsearch version and elastic search version you have downloaded. Have a look at https://github.com/spring-projects/spring-data-elasticsearch/wiki/Spring-Data-Elasticsearch---Spring-Boot---version-matrix for more detail of matrix.
2. modify your configuration file as per your reqirement. like uncomment cluster.name, port,node etc.
3. Run bin/elasticsearch (bin\elasticsearch.bat for window)
4. Build the project with mvn clean install (I've added integration test and should be passed during maven build)

# ES operations
1. create index called twitter
http://localhost:9200/twitter/ using post.
2. add document on twitter
http://localhost:9200/twitter/tweet/1  using post with body:


{
    "tweet" : {
        "user" : "kimchy",
        "post_date" : "2009-11-15T14:12:12",
        "message" : "trying out Elastic Search"
    }
}

3. get document
http://localhost:9200/twitter/tweet/1: kimchy using get
4. search document
http://localhost:9200/twitter/tweet/_search?q=user: kimchy using get


Table 2.1. Supported keywords inside method names, it will be helpful if you want customquery with spring-data-elasticsearch.

Keyword	Sample	    Elasticsearch Query String
1. findByNameAndPrice	{"bool" : {"must" : [ {"field" : {"name" : "?"}}, {"field" : {"price" : "?"}} ]}}
2. findByNameOrPrice	{"bool" : {"should" : [ {"field" : {"name" : "?"}}, {"field" : {"price" : "?"}} ]}}
3. findByName	{"bool" : {"must" : {"field" : {"name" : "?"}}}}
4. findByNameNot	{"bool" : {"must_not" : {"field" : {"name" : "?"}}}}
5. findByPriceBetween	{"bool" : {"must" : {"range" : {"price" : {"from" : ?,"to" : ?,"include_lower" : true,"include_upper" : true}}}}}
6. findByPriceLessThan	{"bool" : {"must" : {"range" : {"price" : {"from" : null,"to" : ?,"include_lower" : true,"include_upper" : true}}}}}
7. findByPriceGreaterThan	{"bool" : {"must" : {"range" : {"price" : {"from" : ?,"to" : null,"include_lower" : true,"include_upper" : true}}}}}
8. findByPriceBefore	{"bool" : {"must" : {"range" : {"price" : {"from" : null,"to" : ?,"include_lower" : true,"include_upper" : true}}}}}
9. findByPriceAfter	{"bool" : {"must" : {"range" : {"price" : {"from" : ?,"to" : null,"include_lower" : true,"include_upper" : true}}}}}
10. findByNameLike	{"bool" : {"must" : {"field" : {"name" : {"query" : "?*","analyze_wildcard" : true}}}}}
11. findByNameStartingWith	{"bool" : {"must" : {"field" : {"name" : {"query" : "?*","analyze_wildcard" : true}}}}}
12.	findByNameEndingWith	{"bool" : {"must" : {"field" : {"name" : {"query" : "*?","analyze_wildcard" : true}}}}}
13. findByNameContaining	{"bool" : {"must" : {"field" : {"name" : {"query" : "*?*","analyze_wildcard" : true}}}}}
14. findByNameIn(Collection<String>names)	{"bool" : {"must" : {"bool" : {"should" : [ {"field" : {"name" : "?"}}, {"field" : {"name" : "?"}} ]}}}}
15. findByNameNotIn(Collection<String>names)	{"bool" : {"must_not" : {"bool" : {"should" : {"field" : {"name" : "?"}}}}}}
16. findByStoreNear	Not Supported Yet !
17. findByAvailableTrue	{"bool" : {"must" : {"field" : {"available" : true}}}}
18. findByAvailableFalse	{"bool" : {"must" : {"field" : {"available" : false}}}}
19. findByAvailableTrueOrderByNameDesc	{"sort" : [{ "name" : {"order" : "desc"} }],"bool" : {"must" : {"field" : {"available" : true}}}}

