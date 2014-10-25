To run the wildfly alone:

ubuntu@ip-10-102-171-117:~$ fig -f wildfly-fig.yml up -d wildfly
Recreating ubuntu_wildfly_1...
ubuntu@ip-10-102-171-117:~$ fig -f wildfly-fig.yml ps
      Name               Command          State                                                   Ports                                                  
--------------------------------------------------------------------------------------------------------------------------------------------------------
ubuntu_wildfly_1   /usr/bin/supervisord   Up      22/tcp, 0.0.0.0:8009->8009/tcp, 0.0.0.0:8080->8080/tcp, 0.0.0.0:9001->9001/tcp, 0.0.0.0:9990->9990/tcp 
ubuntu@ip-10-102-171-117:~$ fig -f wildfly-fig.yml stop
Stopping ubuntu_wildfly_1...
ubuntu@ip-10-102-171-117:~$ fig -f wildfly-fig.yml rm
Going to remove ubuntu_wildfly_1
Are you sure? [yN] y
Removing ubuntu_wildfly_1...
ubuntu@ip-10-102-171-117:~$
