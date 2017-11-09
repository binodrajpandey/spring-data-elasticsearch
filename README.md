# spring-data-elasticsearch

To run this application, Please follow the following instructions.
1. Download Elastic Search zip file from https://www.elastic.co/downloads/elasticsearch and put it in any location of your pc and extract it.
Note: you have to match spring-boot-version, spring-data-elasticsearch version and elastic search version you have downloaded. Have a look at https://github.com/spring-projects/spring-data-elasticsearch/wiki/Spring-Data-Elasticsearch---Spring-Boot---version-matrix for more detail of matrix.
2. modify your configuration file as per your reqirement. like uncomment clusteer.name etc.
3. run elasticsearch.bat file under bin folder
4. build the project with mvn clean install (I've added integration test andd should be passed during build)
