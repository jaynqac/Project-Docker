# Project-Docker

1. Clone github repository using:

  $ sudo git clone https://github.com/jaynqac/Project-Docker

2. Change directory into the created folder after cloning
  for example:
  $ cd /home/Project-Docker 

3. Run the docker compose file:

  $ sudo docker-compose up

4. This should install all the tools and spin up individual containers for each tool
Tools configured:
  - Java ( base image )
  - Jenkins
  - Jira
  - Nexus
  - TomCat
  - Zabbix (broken)
  - PostFix (incomplete)
  - UrbanCode Deploy (not started)
  - Puppet Enterprise (did not get to)

5. Execute the following command to check the ports assigned to the tools or check the ports in the docker-compose.yml file

  $ docker ps

6. To check that the container is running, enter the following URL template and replace your IP Address followed by the Port Number
  e.g. 
  http://YourIpAddressHere:PortNumber
