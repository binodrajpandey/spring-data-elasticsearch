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
http://localhost:9200/twitter/tweet/1 kimchy using post with body 
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
