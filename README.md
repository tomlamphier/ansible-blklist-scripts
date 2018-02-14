# ansible-blklist-scripts
This repo contains an Ansible playbook to install scripts and conf files for the blklist project ([See article on blog.](http://datasciex.com/?p=161)).

## File List

| File                | Description                           |
| ------------------- | ------------------------------------- |
| nginxstream.conf    | Configure Flume to stream log file.   |
| start-flume         | Run Flume.                            |
| stop-flume          | Quit Flume.                           |
| start-spark         | Run Java program under Spark.         |
| stop-spark          | Quit Spark.                           |         
| nginx.conf          | Conf file to use Lua scripting.       |         
| ip_blacklist.lua    | Lua script.                           |         


## Prerequisites
1. A control computer (local or dedicated server) with Ansible, Maven, Git, and Jenkins.
2. (optional) A local computer to connect to your dedicated server.
3. A running AWS instance with Amazon linux, a public IP address,  and an SSH key pair.
3. A file copy of the private SSH key on your local computer.

## Installation

1. Clone this repo on your control computer:

        git clone http://github.com/tomlamphier/ansible-blklist-scripts.git
2. Copy the SSH private key to the project directory. Use the scp command to copy the file if you are working with a dedicated server.
3. Edit the hosts file; replace the xxx's with the public IP for the target AWS instance; set ansible_ssh_private_key_file variable to point to your private key.
4. Update the connect script to point to the private SSH key and the target AWS instance. Run it as a quick test of your connectivity to the AWS instance:

        ./connect
You should get an auth message on the first pass--simply say 'yes'.  If you see the AWS Amazon Linux welcome message, you are OK. Use logout to exit.

5. Run the playbook:

        ansible-playbook -i hosts playbook.yml

   This will install everything on the target computer.


