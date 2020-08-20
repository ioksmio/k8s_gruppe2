
# Assignment: DNS Round Robin Test

***

In this assignment you will use multiple created networks to respond to one DNS address. 

1. Create a network named "msi"

2. Create two Elastic Search Containers from the Image ```elasticsearch:2```. Kindly ensure when creating the images to use the option ```–network-alias search``` to give the containers an additional DNS name to respond to

3. Run a container from an alpine image with the command ```nslookup``` to verify the ip addresses that respond to the alias ```search.network```

4. Run a container from a centos image with the command ```curl –s search:9200``` on the msi network and monitor whether the output changes (check "name", Elasticsearch names itself differently whenever a container is started) everytime you rerun the container.  

***

# Solution to Assignment

```
1.
docker network create msi
docker network ls


```
2.
docker container run –d -–net msi -–net-alias search elasticsearch:2
docker container ls

```
3.
docker container run --rm --net msi alpine nslookup search.msi

```
4.
docker container run --rm --net msi centos curl -s search:9200
docker container ls

```

