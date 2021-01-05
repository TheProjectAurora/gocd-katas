# GoCD demo
This repositry include www.gocd.org demo that setup is as a sandbox.

# Pipelines Groups
- System Smoke -> Test just does GoCD<=>Docker connection work smoothly
- Components -> Include SW components pipelines
- SubStacks -> Is pipeline of pipeline that include SW components integrations with integration testing
- Applicaion -> Is pipeline of pipeline that include SubStack and Component-C integration to working application with integration testing

![Architecture of pipelines](./pictures/pipelines.jpg)

# Setup / Usage
1. Unix socker privialedges so elastic docker agents could be started: ```chmod 777 /var/run/docker.sock```
1. System write data to ./DATA folder so it need wide access to there: ```chmod -R 777 ./DATA```
1. Start:  ```docker-compose up -d```
1. http://localhost:8153 should answer (Note. First execution could show ERROR that is temporaty and fixed automaticly, second round not show it)
1. In DASHBOARD you can see individual pipelines.
1. When you click VSM in DASHBOARD then you can see pipeline of pipeline integrations. 

# Clean
1. Stop:  ```docker-compose down```
1. Remove Data:  ```rm -Rf ./DATA```
1. Prepare to new round:  ```git checkout ./DATA```
1. Restart you docker daemon so it turn /var/run/docker.sock privialedges back to normal.

# DEVELOPMENT
1. Do development by using branch
1. Change branch to docker-compose.yaml and to all pipeline files in pipelines_yamls folder
1. When you merge branch to main then remember change branch to main to all of those places