##Mesos Slave images

Mesos accepts all variables that are assigned on the command line as environment variables.
Use MESOS_{VAIRABLE}


#Ubuntu
e.g
	docker run -d \
	-e MESOS_HOSTNAME=ip.address \
	-e MESOS_IP=ip.address \
	-e MESOS_MASTER=zk://node-1:2181,node-2:2181,node-3:2181/mesos \
	-v /sys/fs/cgroup:/sys/fs/cgroup \
	-v /var/run/docker.sock:/var/run/docker.sock \
	--name slave --net host --privileged --restart always \
	synopsiopublic/mesos-slave:0.24.1-ubuntu14.04
