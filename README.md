---
# Assignment 1:

---

# Instructions on how we setup Azure:
- We chose our resource as Ubuntu server.
- Provided the Virtual machine's name as manishev and gave the disk type as a SSD and then created username and static password instead of SSH for our vm.
- Then we created a new resource group as datagroup and chose our location as East US.
- We select our virtual machine's configuration i.e. 4 GB ram and 8 gb SSD Storage.
- We then setup the network for hte virtual machine and made a static public IP address and made an inbound port rule for port 9200 and deployed the VM.
- For SSH connection we used PuTTY and connected through our static public IP address.
- We then installed elastic search by using the command's:
_wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -_ (Import elasticsearch's public GPG key).
- _sudo apt-get install apt-transport-https_ (Enabling HTTP transport)
- _sudo apt-get update_ (Update apt package)
- _sudo apt-get -y install elasticsearch_ (To install Elastic Search)
- _sudo nano /etc/elasticsearch/elasticsearch.yml_ (To update the configuration file by updating the node name and cluster name and network host)
- _sudo update-rc.d elasticsearch defaults 95 10_(To run elasticsearch on start up)
- Then we started the elastic search service using the command:
 _sudo service elasticsearch start_



***


## ElasticSearch Code:

- a)

```
{"query":{
"match_phrase":{
"name_stop":"ridge Valley Rd in front of civic address 39"}},"_source":["stop_id"]}

{"query":{
"match_phrase":{
"stop_id":"8167"}},"_source":["trip_id"]}

{"query":{
"match_phrase":{
"trip_id":"6518007-2012_05M-1205BRsu-Sunday-02"}},"_source":["trip_headsign"]}

```
- b)
```
{   "query": {  
    "range" : {
        "arrival_time" : {
            "gte": "18:27:00", 
            "lte": "20:55:00",  
            "format": "HH:mm:ss"
        }
    }}}


{"query":{
"match_phrase":{
"trip_id":"6528747-2012_08A-1208BRsa-Saturday-01"}},"_source":["trip_headsign"] }

```
- c)
```
{   "query": {  
    "range" : {
        "arrival_time" : {
            "gte": "18:27:00", 
            "lte": "20:55:00",  
            "format": "HH:mm:ss"
        }
    }}}


{"query":{
"match_phrase":{
"trip_id":"6528747-2012_08A-1208BRsa-Saturday-01"}},"_source":["trip_headsign"] }

```
- d)
```
{   {"query":{
"match_phrase":{
"name_stop":"south St [westbound] opposite Cataret St"}},"_source":["stop_id"]}

{"query":{
"match_phrase":{
"stop_id":"8302"}},"_source":["stop_sequence"]}


{"sort" : [
        { "stop_sequence" : {"order" : "asc"}}],
 "query": {
  "match_phrase": { "stop_sequence": "2" }  
   }}

```
- e)
```
{"query":{
"match_phrase":{
"stop_id":"8643"}},"_source":["name_stop"]}

{"query":{
"match_phrase":{
"stop_id":"6105"}},"_source":["name_stop"]}

{"query":{
"match_phrase":{"stop_id":"6108"}},"_source":["name_stop"]}


```



