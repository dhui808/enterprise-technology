## Get the MQ in Docker image
	docker pull ibmcom/mq:latest
	docker images

## Run the container from the image
	To avoid losing the queue manager and queue data when the container is deleted, use Docker volumes.
	docker volume create qm1data
	Run the MQ server container (Edit the command to set your own password):
	docker run --env LICENSE=accept --env MQ_QMGR_NAME=QM1 --volume qm1data:/mnt/mqm --publish 1414:1414 --publish 9443:9443 --detach --env MQ_APP_PASSWORD=passw0rd ibmcom/mq:latest
	docker exec -ti ba7694cd4a96 /bin/bash
	Display the MQ installation and data paths:
	dspmqver
	Display your running queue managers
	dspmq
	To come out of the Docker container and return to your command line, type exit and press Enter
	
	Inside the container, the MQ installation on RHEL has the following objects:

		Queue manager QM1
		Queue DEV.QUEUE.1
		Channel: DEV.APP.SVRCONN
		Listener: SYSTEM.LISTENER.TCP.1 on port 1414
		
	user “app”, who is a member of the group “mqclient” is permitted to use the channel DEV.APP.SVRCONN to 
	connect to the queue manager QM1 and is authorized to put and get messages to and from the queue DEV.QUEUE.1.
