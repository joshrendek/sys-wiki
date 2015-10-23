Docker
========

### CI Disk Space

``` 01 * * * * docker rm $(docker ps -a -q); docker rmi $(docker images | grep '<none>' | tr -s ' ' | cut -d ' ' -f 3) ```
