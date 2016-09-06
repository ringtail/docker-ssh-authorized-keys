# docker-ssh-authorized-keys
<a href="https://cs.console.aliyun.com/#/app/create/step1" target="_blank"><img src="http://moyuan.oss-cn-beijing.aliyuncs.com/github/icon.png"  width=108px/></a>

## Info  
In some distributed programs such as tsung, we need to add a ssh tunnel between master and slaves. In the master container. you can ssh to any of slave without password validation.

## Usage   

1.create new ssh key pair 

	ssh-keygen -t rsa -P""

2.open the ssh key pairs path   
	
	open ~/.ssh   
	
3.add private key to master 
	
	// upload ~/.ssh/id_rsa to ECS or you can use oss volume driver
	// change the path of docker-compose.yml   
	
	${your private key path}:/root/.ssh/id_rsa    
	
4.add public key to slave then copy the output to docker-compose.yml   
	
	cat ~/.ssh/id_rsa.pub   

## Test  
			
	// login to the master 
	ssh masterIp -Pport 
	
	// then jump to the slave.
	ssh slaveIp    
	
	
