# Jira + Confluence Docker Compose

Agent [atlassian-agent.jar](https://gitee.com/pengzhile/atlassian-agent/releases) need to put the in root catalog.

## install
```
git clone git@github.com:DenoBY/jira-confluence.git
cd jira-confluence
wget https://gitee.com/pengzhile/atlassian-agent/attach_files/832833/download/atlassian-agent-v1.3.1.zip
unzip atlassian-agent-v1.3.1.zip
mv atlassian-agent-v1.3.1/atlassian-agent.jar .
cd ..
docker-compose up -d 
```

## activation jira
```
docker exec -it <container_id> bash

cd /opt/atlassian/jira/
java -jar atlassian-agent.jar \
	-d -m test@test.com -n BAT \
  	-p jira -o http://localhost:7000 \
  	-s <server_id>
```

## activation confluence
```
docker exec -it <container_id> bash

cd /opt/atlassian/confluence
java -jar atlassian-agent.jar \
	-d -m test@test.com -n BAT \
  	-p conf -o http://localhost:7005/ \
  	-s <server_id>
```
