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

4.Run Studio 3T for MongoDB and connect to localhost:27017

