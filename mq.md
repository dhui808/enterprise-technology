## Get the MQ in Docker image
	docker pull ibmcom/mq:latest
	docker pull ibmcom/mq:latest

## Run the container from the image
	To avoid losing the queue manager and queue data when the container is deleted, use Docker volumes.
	docker volume create qm1data
	Run the MQ server container (Edit the command to set your own password):
	docker run --env LICENSE=accept --env MQ_QMGR_NAME=QM1 --volume qm1data:/mnt/mqm --publish 1414:1414 --publish 9443:9443 --detach --env MQ_APP_PASSWORD=passw0rd ibmcom/mq:latest
	docker exec -ti ba7694cd4a96 /bin/bash 
