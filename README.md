# HDPAdmin1Plus
- [Lab 1](https://github.com/HortonworksUniversity/HDPAdmin1Plus#lab-1)
  - Access cluster
  - 
  
---------------

# Lab 1

## Accessing your Cluster

Credentials will be provided for these services by the instructor:

* SSH
* Ambari

## Use your Cluster

### To connect using Putty from Windows laptop

- Download ppk from [here](https://github.com/HortonworksUniversity/HDPAdmin1Plus/master/training-keypair.ppk)
- Use putty to connect to your node using the ppk key:
  - Connection > SSH > Auth > Private key for authentication > Browse... > Select training-keypair.ppk
![Image](https://raw.githubusercontent.com/HortonworksUniversity/HDPAdmin1Plus/master/screenshots/putty.png)

- Make sure to click "Save" on the session page before logging in

## Now you are ready to proceed to the Installing HDP Lab
### To connect from Linux/MacOSX laptop

- SSH into Ambari node of your cluster using below steps:
  - Right click [this pem key](https://raw.githubusercontent.com/HortonworksUniversity/HDPAdmin1Plus/master/training-keypair.pem)  > Save link as > save to Downloads folder
  - Copy pem key to ~/.ssh dir and correct permissions
  ```
  cp ~/Downloads/training-keypair.pem ~/.ssh/
  chmod 400 ~/.ssh/training-keypair.pem
  ```
 - Login to the Ambari node of the cluster you have been assigned by replacing IP_ADDRESS_OF_AMBARI_NODE below with Ambari node IP Address (your instructor will provide this)   
  ```
  ssh -i  ~/.ssh/training-keypair.pem centos@IP_ADDRESS_OF_AMBARI_NODE
  ```
  - To change user to root you can:
  ```
  sudo su -
  ```

- Similarly login via SSH to each of the other nodes in your cluster as you will need to run commands on each node in a future lab

- Tip: Since in the next labs you will be required to run *the same set of commands* on each of the cluster hosts, now would be a good time to setup your favorite tool to do so: examples [here](https://www.reddit.com/r/sysadmin/comments/3d8aou/running_linux_commands_on_multiple_servers/)
  - On OSX, an easy way to do this is to use [iTerm](https://www.iterm2.com/): open multiple tabs/splits and then use 'Broadcast input' feature (under Shell -> Broadcast input)
  - If you are not already familiar with such a tool, you can also just run the commands on the cluster, one host at a time

#### Login to Ambari

- Login to Ambari web UI by opening http://AMBARI_PUBLIC_IP:8080 and log in with admin/BadPass#1

- You will see a Ambari's Management Page showing no clusters running. 

- Instructor will provide you with 4 AWS Instances with Public IP addresses and Private IP addresses.

#### Login to all four of your nodes using ssh client or PuTTy if you are using Microsoft Windows.
```
$ ssh –i training-keypairs.pem centos@<YOUR EXTERNAL IP ADDRESS>
```

Switch users to root
```
$ sudo su –
```
# 

Edit the /etc/hosts files on each node and add the following entries

### THIS IS A EXAMPLE – YOUR IP's WILL BE DIFFERENT
```
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

172.30.0.137  node1
172.30.0.34   node2
172.30.0.35   node3
172.30.0.36   node4
```
Reset set the hostname on each node – all nodes for example

On first node – 172.30.0.137
```
# hostname node1
```
On second node – 172.30.0.34
```
# hostname node2
```
On third node – 172.30.0.35
```
# hostname node3
```
On forth node – 172.30.0.36
```
# hostname node4
```
Verify hostname have been updated on each node
```
# hostname
```
node1

Restart ambari-agent on each node
```
# ambari-agent restart
```
Exit from root on the ambari node – node1
```
# exit
$
```
### Now you are ready for the next lab "Installing HDP"
