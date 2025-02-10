For this project, we shall use Ansible to deploy Nexus to Ubuntu server, similar to the following commands, if it was deployed manually.

Manual way:

apt-get update
apt install openjdk-8-jre-headless
apt install net-tools

cd /opt
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
tar -zxvf latest-unix.tar.gz

adduser nexus
chown -R nexus:nexus nexus-3.65.0-02
chown -R nexus:nexus sonatype-work

vim nexus-3.65.0-02/bin/nexus.rc
run_as_user="nexus"

su - nexus
/opt/nexus-3.65.0-02/bin/nexus start

ps aux | grep nexus #check if nexus is running
netstat -lnpt #outputs result of checking

---

Instructions:

1. Deploy Ubuntu server (from any cloud provider with public access)
2. Amend the 'hosts' file with the public IP of the deployed server and location of your private key.
3. In command line, run 'ansible-playbook deploy-nexus.yaml'

Note:

- Do not amend anything in YAML file. Everything should run as intended.
