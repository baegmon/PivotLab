# PivotLab

A docker environment to practice pivoting. Used to practice port forwarding techniques as well as any tools such as SSHUTTLE.

The environment creates two networks:
1. DMZ Network
    A network where the SSH server will sit in (172.16.0.0/24)
2. Pivot Network
    An internal network that can be accessed from the gateway. (172.16.1.0/24)

The environment creates two containers:
1. SSH Server
    Just a simple SSH server that acts as the gateway into the internal environment.
2. Web Server
    A simple webserver on port 80, working as the target that you want to reach. This host is placed in the *Pivot Network* and can only be accessed via the *SSH Server*.

Instructions:
1. Observe that you cannot access or ping the webserver.
2. SSH into the SSH Server container:
```ssh user@172.16.0.10 -p 2222``` 
3. Ping the webserver and observe requests are coming through (observing segregated network)
```sudo ping webserver``` or ```sudo ping 172.16.1.12```
4. Use this knowledge to test out port forwarding or SSHUTTLE by using the SSH Server. You can also modify the ```docker-compose.yml``` file to create more complex pivot environments.