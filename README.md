# ASP.NET-Web-API-for-MongoDB-with-identity-and-JWT

1. Run Docker Desktop

![image](https://github.com/user-attachments/assets/c8e119df-b388-49f7-a06b-9aad7c74aaa3)

2. Create a new network

```
docker network create mongoCluster
```

3. Create new MongoDb replica: 

```
docker run -d --rm -p 27017:27017 --name mongo1 --network mongoCluster mongo:latest mongod --replSet myReplicaSet --bind_ip localhost,mongo1
docker run -d --rm -p 27018:27017 --name mongo2 --network mongoCluster mongo:latest mongod --replSet myReplicaSet --bind_ip localhost,mongo2
docker run -d --rm -p 27019:27017 --name mongo3 --network mongoCluster mongo:latest mongod --replSet myReplicaSet --bind_ip localhost,mongo3
```

```
docker exec -it mongo1 mongosh --eval "rs.initiate({ _id: 'myReplicaSet', members: [{_id: 0, host: 'mongo1', priority: 3}, {_id: 1, host: 'mongo2', priority: 2}, {_id: 2, host: 'mongo3', priority: 1}]})"
```

4. Run Studio 3T for MongoDB and connect to localhost:27017

5. Run these commands to verify the installation

```
docker exec -it mongo1 mongosh --eval 'rs.status()'
```

```
docker exec -it mongo1 mongosh --eval 'rs.printReplicationInfo()'
```

6. Run Studio 3T for MongoDB

![image](https://github.com/user-attachments/assets/dfa76885-8c17-41e5-8d08-1df6960f7660)

7. Create the connection string in Studio 3T for MongoDB

![image](https://github.com/user-attachments/assets/80704dee-c25b-4f61-8b80-0f9409b41af3)

8. Verify the connection pressing on the Test Connection button

![image](https://github.com/user-attachments/assets/6e412c5e-e0a8-4bd2-9c3d-0905002ad410)

![image](https://github.com/user-attachments/assets/62e5f6e5-ac80-40bd-958a-455640e7b7cc)

9. Set the connection name and save it

![image](https://github.com/user-attachments/assets/d3e2ad23-13fa-4d13-8af9-c3185825f90d)


 



