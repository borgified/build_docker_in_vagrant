This Vagrantfile sets up an environment that allows you to build Docker images under Jenkins.

- vagrant up
- browse to http://localhost:8080
- vagrant ssh, sudo cat /var/lib/jenkins/secrets/initialAdminPassword
- you can skip installing plugins if you want

Test it out

- create a freestyle project
- under build section, execute shell, put this in:
```
echo "FROM ubuntu:16.04" > Dockerfile
docker build .
```

This creates a dummy Dockerfile and runs the docker build on it to show that it works.

Console Output should look like this:
```
Started by user admin
Building in workspace /var/lib/jenkins/workspace/a
[a] $ /bin/sh -xe /tmp/jenkins8119501228670825707.sh
+ echo FROM ubuntu:16.04
+ docker build .
Sending build context to Docker daemon  2.048kB

Step 1/1 : FROM ubuntu:16.04
16.04: Pulling from library/ubuntu
18d680d61657: Pulling fs layer
0addb6fece63: Pulling fs layer
78e58219b215: Pulling fs layer
eb6959a66df2: Pulling fs layer
eb6959a66df2: Waiting
0addb6fece63: Verifying Checksum
0addb6fece63: Download complete
78e58219b215: Verifying Checksum
78e58219b215: Download complete
18d680d61657: Verifying Checksum
18d680d61657: Download complete
eb6959a66df2: Verifying Checksum
eb6959a66df2: Download complete
18d680d61657: Pull complete
0addb6fece63: Pull complete
78e58219b215: Pull complete
eb6959a66df2: Pull complete
Digest: sha256:76702ec53c5e7771ba3f2c4f6152c3796c142af2b3cb1a02fce66c697db24f12
Status: Downloaded newer image for ubuntu:16.04
 ---> 4a689991aa24
Successfully built 4a689991aa24
Finished: SUCCESS
```

