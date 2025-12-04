# Starting a Container

To begin, I started a container in detached mode using the following command:
```
docker run -d --name logout nginx:latest
```
Actually 2 conatiners
<img width="1322" height="97" alt="Screenshot 2025-12-04 163029" src="https://github.com/user-attachments/assets/929de2f3-8881-4d09-aa41-fcc88bc4532c" />
### Logging Into a Running Container

To access the shell of a running container, I used the following command:
```
docker exec -it login /bin/bash
```
and install ping in container
```
apt-get install iputils-ping -y
```
<img width="1447" height="409" alt="Screenshot 2025-12-04 163406" src="https://github.com/user-attachments/assets/6ceedb3e-9856-475f-9125-022183f696a7" />
### To view detailed information about a container, including its IP address, I used:
```
docker inspect <container_name>
```
<img width="1339" height="634" alt="Screenshot 2025-12-04 163534" src="https://github.com/user-attachments/assets/9609aa6e-f084-4597-ac9b-c49f77ccd8ce" />

then ping is successfull beacuse both containers are using the same Veth.
<img width="912" height="142" alt="Screenshot 2025-12-04 163611" src="https://github.com/user-attachments/assets/e9dd2a33-c685-4096-98de-932732eabcc6" />

# Creating a Container on a Custom Network

To run a container on a user-defined network, I used:
```
docker run -d --name finance --network=first-network nginx:latest
```
<img width="959" height="147" alt="Screenshot 2025-12-04 165045" src="https://github.com/user-attachments/assets/6ce075e0-ae19-41d6-a1fa-7e0aa2f4bd69" />

# Container Communication Across Networks

Currently, three containers are running: two are on the same network, and the third (finance) is on a different network.

Containers on the same network can communicate and ping each other successfully.

The finance container, being on a different network, cannot reach the others because it uses a separate virtual Ethernet interface (veth), ensuring network isolation.

<img width="1332" height="473" alt="Screenshot 2025-12-04 165529" src="https://github.com/user-attachments/assets/3a60f6f8-7195-4ebb-affd-14763b317c40" />




