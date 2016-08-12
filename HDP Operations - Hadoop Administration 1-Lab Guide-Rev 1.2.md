- HDP Operations:

- Hadoop Administration 1

- Lab Guide

- Rev 1.2

![Im1](images/Im1)

![Im0](images/Im0)

![Im0](images/Im0)

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

The contents of this course and all its lessons and related materials, including handouts to

audience members, are Copyright © 2012 - 2016 Hortonworks, Inc.

No part of this publication may be stored in a retrieval system, transmitted or reproduced in anyway,  including,  but  not  limited  to,  photocopy,  photograph,  magnetic,  electronic  or  other  record,without the prior written permission of Hortonworks, Inc.

This instructional program, including all material provided herein, is supplied without any

guarantees from Hortonworks, Inc. Hortonworks, Inc. assumes no liability for damages or legalaction arising from the use or misuse of contents or details contained herein.

Linux® is the registered trademark of Linus Torvalds in the United States and other countries.Java® is a registered trademark of Oracle and/or its affiliates.

All other trademarks are the property of their respective owners.

Copyright Hortonworks Inc. 2012 – 2016. All Rights Reserved

![Im1](images/Im1)

![Im2](images/Im2)

Become a Hortonworks Certified Professional and establish your credentials:

• HDP Certified Developer: for Hadoop developers using frameworks like Pig, Hive, Sqoop andFlume.

• HDP Certified Administrator: for Hadoop administrators who deploy and manage Hadoop

clusters.

• HDP Certified Developer: Java: for Hadoop developers who design, develop and architect

Hadoop-based solutions written in the Java programming language.

• HDP Certified Developer: Spark: for Hadoop developers who write and deploy applications forthe Spark framework.

• HDF Certified Professional: for DataFlow Operators responsible for building and deploying

HDF workflows.

How to Register: Visit www.examslocal.com and search for “Hortonworks” to register for an

exam. The cost of each exam is $250 USD, and you can take the exam anytime, anywhere

using your own computer. For more details, including a list of exam objectives and instructionson how to attempt our practice exams, visit http://hortonworks.com/training/certification/

Earn Digital Badges:  Hortonworks Certified Professionals receive a digital badge for each

certification earned. Display your badges proudly on your résumé, LinkedIn profile, email

signature, etc.

Copyright Hortonworks Inc. 2012 – 2016. All Rights Reserved

![Im0](images/Im0)

![Im0](images/Im0)

Self Paced Learning Library

On Demand Learning

Hortonworks University Self-Paced Learning Library is an on-demand dynamic repositoryof content that is accessed using a Hortonworks University account.  Learners can viewlessons anywhere, at any time, and complete lessons at their own pace. Lessons can bestopped and started, as needed, and completion is tracked via the Hortonworks UniversityLearning Management System.

Hortonworks University courses are designed and developed by Hadoop experts and

provide an immersive and valuable real world experience. In our scenario-based trainingcourses, we offer unmatched depth and expertise.  We prepare you to be an expert withhighly valued, practical skills and prepare you to successfully complete Hortonworks

Technical Certifications.

Target Audience:  Hortonworks University Self-Paced Learning Library is designed forthose new to Hadoop, as well as architects, developers, analysts, data scientists, and ITdecision makers. It is essentially for anyone who desires to learn more about Apache

Hadoop and the Hortonworks Data Platform.

Duration:  Access to the Hortonworks University Self-Paced Learning Library is providedfor a 12-month period per individual named user. The subscription includes access to over400 hours of learning lessons.

The online library accelerates time to Hadoop competency. In addition, the content is

constantly being expanded with new material, on an ongoing basis.

Visit: http://hortonworks.com/training/class/hortonworks-university-self-paced-learning-

library/

Copyright Hortonworks Inc. 2012 – 2016. All Rights Reserved

Table of Contents

- Lab: Managing Ambari Users and Groups ................................................................................................ 1

- About This Lab ........................................................................................................................................ 1

- Connecting to the Lab Environment ...................................................................................................... 1

- Starting the Cluster ................................................................................................................................. 2

- Viewing Hadoop Service Accounts ........................................................................................................ 3

- Adding Ambari User Accounts ............................................................................................................... 4

- Assign User Account Permissions ......................................................................................................... 7

- Testing User Account Functionality ....................................................................................................... 7

- Creating New Groups ........................................................................................................................... 14

- Testing Interaction Between User and Group Permissions ................................................................ 17

- Result ..................................................................................................................................................... 19

- Lab: Managing Hadoop Services ............................................................................................................. 21

- About This Lab ...................................................................................................................................... 21

- Viewing Hadoop Service Configuration Files ....................................................................................... 21

- Ambari Web UI Management and Configuration Features ................................................................. 22

- Changing HDFS Service Configuration ................................................................................................ 25

- Creating an Ambari Configuration Group ............................................................................................ 30

- Downloading HDFS Configuration Files ............................................................................................... 34

- Result ..................................................................................................................................................... 35

- Lab: Using Hadoop Storage ..................................................................................................................... 37

- About This Lab ...................................................................................................................................... 37

- Exploring HDFS Shell ............................................................................................................................ 37

- Using the HDFS Shell ............................................................................................................................ 38

- Overriding Default HDFS Properties .................................................................................................... 41

- Configuring Ambari Files View ............................................................................................................. 42

- Using the NameNode UI File Browser .................................................................................................. 49

- Result ..................................................................................................................................................... 52

- Lab: Using WebHDFS ............................................................................................................................... 53

- About This Lab ...................................................................................................................................... 53

- Verifying WebHDFS is Enabled ............................................................................................................ 53

- Using WebHDFS API Commands ......................................................................................................... 54

- Result ..................................................................................................................................................... 56

- Lab: Using HDFS Access Control Lists ................................................................................................... 57

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

- About This Lab ...................................................................................................................................... 57

- Configuring HDFS ACLs ....................................................................................................................... 57

- Managing File ACLs .............................................................................................................................. 59

- Managing Directory ACLs ..................................................................................................................... 62

- Managing Access Using an Access Mask ........................................................................................... 64

- Result ..................................................................................................................................................... 65

- Lab: Managing Hadoop Storage .............................................................................................................. 67

- About This Lab ...................................................................................................................................... 67

- Managing and Monitoring with Ambari ................................................................................................ 67

- Managing and Monitoring with Commands ......................................................................................... 73

- Checking HDFS Consistency ............................................................................................................... 75

- Viewing a Block Scanner Report .......................................................................................................... 77

- Result ..................................................................................................................................................... 78

- Lab: Managing HDFS Quotas .................................................................................................................. 79

- About This Lab ...................................................................................................................................... 79

- Creating a Directory .............................................................................................................................. 79

- Assigning Quotas .................................................................................................................................. 80

- Testing Quotas ...................................................................................................................................... 81

- Result ..................................................................................................................................................... 82

- Lab: Managing the YARN Service Using Ambari Web UI ....................................................................... 83

- About This Lab ...................................................................................................................................... 83

- Exploring the Ambari Web UI ............................................................................................................... 83

- Changing YARN Service Configuration ................................................................................................ 90

- Result ..................................................................................................................................................... 93

- Lab: Managing the YARN Service Using the CLI .................................................................................... 95

- About This Lab ...................................................................................................................................... 95

- YARN CLI User Commands .................................................................................................................. 95

- YARN CLI Administrator Commands ................................................................................................... 97

- YARN API Calls ..................................................................................................................................... 97

- Result ..................................................................................................................................................... 98

- Lab: Running Sample YARN Applications ............................................................................................... 99

- About This Lab ...................................................................................................................................... 99

- Running YARN Applications from the CLI ........................................................................................... 99

- Using Ambari Pig View ........................................................................................................................ 102

- Using Ambari Hive View ...................................................................................................................... 111

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

- Result ................................................................................................................................................... 117

- Lab: Adding, Decommissioning, and Recommissioning Worker Nodes ............................................. 119

- About This Lab .................................................................................................................................... 119

- Adding Worker Nodes ......................................................................................................................... 119

- Decommissioning Worker Nodes ....................................................................................................... 125

- Recommissioning Worker Nodes ....................................................................................................... 130

- Turning Off Maintentance Mode ......................................................................................................... 134

- Changing the Replication Factor ........................................................................................................ 135

- Viewing DataNode and Replication Information ................................................................................ 136

- Rebalancing HDFS Storage ................................................................................................................ 139

- Result ................................................................................................................................................... 142

- Lab: Setting Up for Capacity Scheduler Labs ....................................................................................... 143

- About This Lab .................................................................................................................................... 143

- Creating Home Directories ................................................................................................................. 143

- Creating Linux Groups ........................................................................................................................ 144

- Creating Linux User Accounts ............................................................................................................ 144

- Result ................................................................................................................................................... 145

- Lab: Managing YARN Containers and Queues ..................................................................................... 147

- About This Lab .................................................................................................................................... 147

- Lab Preparation ................................................................................................................................... 147

- Comparing Resource Usage .............................................................................................................. 150

- Testing Queue Settings and Behavior ................................................................................................ 153

- Configure queues to meet SLA requirements ................................................................................... 160

- Result ................................................................................................................................................... 169

- Lab: Managing YARN ACLs and User Limits ........................................................................................ 171

- About This Lab .................................................................................................................................... 171

- Lab Preparation ................................................................................................................................... 171

- Configuring YARN ACLs and Default Queue Mapping ...................................................................... 173

- Testing User Limits ............................................................................................................................. 178

- Re-establishing Default Queue Access ............................................................................................. 181

- Result ................................................................................................................................................... 183

- Lab: Configuring Rack Awareness ......................................................................................................... 185

- About This Lab .................................................................................................................................... 185

- Viewing Rack Awareness Information ................................................................................................ 185

- Configuring Rack Awareness ............................................................................................................. 186

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

- Viewing Results of the Configuration ................................................................................................. 189

- Result ................................................................................................................................................... 190

- Lab: Configuring NameNode HA ............................................................................................................ 191

- About This Lab .................................................................................................................................... 191

- Viewing Configurations ....................................................................................................................... 191

- Configuring ZooKeeper ...................................................................................................................... 193

- Enabling NameNode HA. .................................................................................................................... 197

- Verifying HA Configuration. ................................................................................................................ 204

- Testing Failover ................................................................................................................................... 206

- Result ................................................................................................................................................... 209

- Lab: Configuring ResourceManager HA ................................................................................................ 211

- About This Lab .................................................................................................................................... 211

- Viewing ResourceManager Configuration Information ..................................................................... 211

- Verifying the Number of ZooKeeper Servers ..................................................................................... 213

- Enabling ResourceManager HA ......................................................................................................... 213

- Verifying ResourceManager HA configuration .................................................................................. 216

- Testing Failover ................................................................................................................................... 217

- Result ................................................................................................................................................... 220

- Lab: Managing Ambari Alerts ................................................................................................................. 221

- About This Lab .................................................................................................................................... 221

- Listing Alert Definitions ....................................................................................................................... 221

- Working With Alert Definitions ............................................................................................................ 223

- Triggering an Alert ............................................................................................................................... 226

- Creating Alert Groups and Notifications ............................................................................................ 232

- Result ................................................................................................................................................... 239

- Lab: Managing HDFS Snapshots ........................................................................................................... 241

- About This Lab .................................................................................................................................... 241

- Enabling Snapshots ............................................................................................................................ 241

- Managing Snapshots .......................................................................................................................... 242

- Result ................................................................................................................................................... 244

- Lab: Using DistCp ................................................................................................................................... 245

- About This Lab .................................................................................................................................... 245

- Viewing Online DistCp Information .................................................................................................... 245

- Configuring a DistCp test environment. ............................................................................................. 245

- Copying Files and Directories ............................................................................................................ 247

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

- Result ................................................................................................................................................... 248

- Lab: Installing HDP ................................................................................................................................. 249

- About This Lab .................................................................................................................................... 249

- Resetting the Lab Environment .......................................................................................................... 249

- Installing Ambari Server ...................................................................................................................... 249

- Installing HDP ...................................................................................................................................... 251

- Result ................................................................................................................................................... 261

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

- Lab: Managing Ambari Users and Groups

- About This Lab

- Objective:

To manage Ambari users, groups, and permissions in the Ambari Web UI- File locations:

N/A

- Successful outcome:

You will: Connect to your lab environment; log in and start your one-node HDP cluster; view Hadoop service accounts; use the Ambari Web UIto add user accounts; test the functionality of the new user accounts youcreated; create a new Ambari user group and add accounts andpermissions to it; and test the interaction between user permissions andgroup persmissions.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Managing Ambari Users and Groups

- Connecting to the Lab Environment

- Connect to your lab environment.

- 1 .  The lab environment runs inside a single virtual machine.

How you connect to the virtual machine depends on whether you are using a virtual machinerunning on your local desktop system or are connecting to a virtual machine running on acloud service like Amazon Web Services (AWS).

- 2 .  The virtual machine, whether running locally or in the cloud, is running the

Ubuntu Linux operating system and the Docker application.

- 3 .  The Docker application makes it appear as though there are multiple,

CentOS-based systems available for cluster installation.

The CentOS systems are named node1, node2, node3, and node4.

The lab exercises do not use node4.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 4 .  Work with your instructor, as necessary, to determine how to connect to the

Ubuntu desktop on your lab environment virtual machine.

- Starting the Cluster

- Log in and start your pre- installed, one-node HDP cluster.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  On node1, change to the /root/scripts directory and run the env_setup.sh script. This

script ensures that all necessary lab files have been copied and environmental variables havebeen set across the lab nodes. When finished, change back to the root user home directory.- # cd /root/scripts

- # ./env_setup.sh

- # cd ~

- 3 .  Again on node1, use the ambari-server start command to start the Ambari Server.

- # ambari-server start

- 4 .  On node1, user the ambari-agent start command to start the Ambari agent.

- # ambari-agent start

- 5 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 6 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 7 .  Click Services in the Ambari Web UI.

The list of installed services appears on the left side of the Services page and includessuch services has HDFS, MapReduce2, YARN, and others.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 8 .  Click to open and view the Actions menu button and select Start All. This will start all

Hadoop service components in the cluster.

- 9 .  Click Confirm Start to start all cluster service components.

- 10 . Monitor the Start All Services process in the Background Operation Running window. Click OK

to dismiss the window when the process has finished.

- Viewing Hadoop Service Accounts

- View the Hadoop service accounts configured by Ambari during cluster installation.

- Which service accounts are configured depends on the services that were installed by Ambari.

- 1 .  In the terminal window logged in to node1, view the accounts listed in the /etc/passwd file on

node1.

- # cat /etc/passwd

Do you see Hadoop service account names that include

hive, zookeeper, ams, ambari, tez, hdfs, and others?

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 2 .  In the Ambari Web UI, click the Admin menu (not admin) and select Service Accounts.

Do you see a list of the same Hadoop service account names that were listed

in the /etc/passwd file?

- Adding Ambari User Accounts

- Use the Ambari Web UI to add four new Ambari user accounts.

- 1 .  To add a new Ambari user account, select Manage Ambari from the admin menu.

- 2 .  Click Users to open the Users pane.

Ambari displays the current list of user accounts. The list should include only the admin useraccount.

- 3 .  Click +Create Local User.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 4 .  Create a local user account named npuser. Assign this user account the password npuser.

This account will not be assigned any Ambari permissions in this lab exercise. Click Savewhen you are finished.

- 5 .  Create another local user account named rouser and assign it the password rouser. This

account will be assigned read-only permission later in this lab exercise.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 6 .  Create another local user account named opuser and assign it the password opuser. This

account will be assigned operator permission later in this lab exercise.

- 7 .  Create another local user account named aduser and assign it the password aduser. This

account will be assigned Ambari Admin permission as part of the creation process when youconfigure Ambari Admin to Yes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- Assign User Account Permissions

- Assign Ambari permissions to user accounts.

- 1 .  Click Permissions.

- 2 .  In the Operator section beneath Grant permission to these users click Add User, then

click New and type the user account opuser.

In the Read-Only section beneath Grant permission to these users, click Add User,then click New and type the user account rouser.

Click the blue check box icons to confirm and finish adding both users.

- Testing User Account Functionality

- Test the functionality of the four new Ambari user accounts.

- 1 .  Log out of the Ambari Web UI by selecting Sign out from the admin menu.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 2 .  Sign in to the Ambari Web UI using the user name npuser and the password npuser.

The npuser is known to Ambari but has no permissions in Ambari.

Were you able to log in?

What do you see in the browser window?

Do you see the options to navigate to the Dashboard, Services, Hosts , or Alerts pages?Do you see the Ambari Views option?

Are there any Views assigned to the npuser?

- 3 .  Log out of the Ambari Web UI by selecting Sign out from the npuser menu.

- 4 .  Sign in to the Ambari Web UI using the user name rouser and the password rouser.

The rouser account has been assigned read-only permission in Ambari.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

Were you able to log in?

What do you see in the browser window?

Do you see the option to navigate to the Dashboard, Services, Hosts , or Alerts pages?Do you see the Ambari Views option?

Are there any Views assigned to the rouser?

- 5 .  While logged in as rouser, click Dashboard.

Are you able to view Dashboard information?

- 6 .  While logged in as rouser, select HDFS from the Services menu.

Are you able to view HDFS service information on the Summary page?

On the Summary page, do you see the Actions and Service Actions buttons?

Why not?

- 7 .  While logged in as rouser, click Hosts to open the Hosts page.

Are you able to view host information on the Hosts page?

On the Hosts page, do you see the Actions button?

Why not?

- 8 .  While logged in as rouser, click Alerts to open the Alerts page.

Are you able to view host information on the Alerts page?

On the Alerts page, do you see the Actions button?

Why not?

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 9 .  Log out of the Ambari Web UI by selecting Sign out from the rouser menu.

- 10 . Sign in to the Ambari Web UI using the user name opuser and the password opuser.

The opuser has been assigned operator permission in Ambari.

Were you able to log in?

What do you see in the browser window?

Do you see the option to navigate to the Dashboard, Services, Hosts , or Alerts?

Do you see the Ambari Views option?

Are there any Views assigned to the opuser?

Are you also able to see the Admin page listed at the top of the browser window?

This should be the first time that this page is available as an option.

- 11 . While logged in as opuser, click Dashboard.

Are you able to view Dashboard information?

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 12 . While logged in as opuser, select HDFS from the Services menu.

Are you able to view HDFS service information on the Summary page?

On the Summary page, do you see the Actions and Service Actions buttons?

Why?

- 13 . While logged in as opuser, click Hosts to open the Hosts page.

Are you able to view host information on the Hosts page?

On the Hosts page, do you see the Actions button?

Why?

- 14 . While logged in as opuser, click Alerts to open the Alerts page.

Are you able to view alert information on the Alerts page?

On the Alerts page, do you see the Actions button?

Why?

- 15 . Open the opuser menu.

What are the available choices?

Specifically, notice that there is no Manage Ambari menu option.

- 16 . Log out of the Ambari Web UI by selecting Sign out from the opuser menu.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 17 . Sign in to the Ambari Web UI using the user name aduser and the password aduser.

The aduser has been assigned admin permission in Ambari.

Were you able to log in?

What do you see in the browser window?

Do you see the option to navigate to the Dashboard, Services, Hosts , or Alerts pages?Do you see the Ambari Views option?

Are there any Views assigned to the aduser?

Are you able to see the Admin page listed at the top of the browser window?

- 18 . While logged in as aduser, click Dashboard.

Are you able to view Dashboard information?

- 19 . While logged in as aduser, select HDFS from the Services menu.

Are you able to view HDFS service information on the Summary page?

On the Summary page, do you see the Actions and Service Actions buttons?

Why?

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 20 . While logged in as aduser, click Hosts to open the Hosts page.

Are you able to view host information on the Hosts page?

On the Hosts page, do you see the Actions button?

Why?

- 21 . While logged in as aduser, click Alerts to open the Alerts page.

Are you able to view alert information on the Alerts page?

On the Alerts page, do you see the Actions button?

Why?

- 22 . Open the aduser menu.

What are the available choices?

Notice the Manage Ambari menu option, which is only available to user accounts with adminpermission.

- 23 . Select Manage Ambari from the aduser menu.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 24 . Do you see the following?

- 25 . Remain logged in as the aduser.

- Creating New Groups

- Create a new Ambari group named opgroup, add the npuser, rouser, opuser, and

- aduser user accounts to the opgroup group, and assign it the group operator

- permission.

- 1 .  While still logged in as aduser, click Groups to create a new Ambari group.

- 2 .  Click +Create Local Group to create a new local group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 3 .  Type opgroup as the name and click Save.

- 4 .  Click opgroup to add group members.

- 5 .  Click Add User, click New and type npuser, and then click the blue check box to add the

user account to the group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 6 .  Float the mouse pointer over the newly added npuser and notice the pencil icon that appears

to the right.

Click the pencil icon to edit the group and add additional users.

Clicking the pencil icon creates a New text box where you are able to type the name of anotheruser.

Type rouser and click the blue check box to add the user.

- 7 .  Repeat the previous step to add opuser and aduser to opgroup.

All four user accounts should be members of opgroup when you are finished.

- 8 .  Click Permissions to add permissions to the opgroup group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 9 .  In the Operator permission section, add opgroup beneath Grant permissions to these

groups.

Click the blue check box to add the group.

- Testing Interaction Between User and Group Permissions

- Test the interaction between specific user permissions and group permissions.

- 1 .  While still logged in as aduser, click Go to Dashboard to return to the main Ambari Web UI

window.

- 2 .  Click to open the aduser menu.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

Does the aduser account still have the option on this menu to Manage Ambari users, groups,and permissions?

Although the aduser account was added as a member of the opgroup, which has only operatorpermission, has the aduser account lost its admin permission?

- 3 .  Sign out of the aduser account.

- 4 .  Sign in to the Ambari Web UI using the user name npuser and the password npuser.

The npuser is known to Ambari but has no permissions in Ambari.

However, the npuser account was added as a member of the opgroup group, which hasoperator permissions.

What do you see in the browser window?

Do you see the option to navigate to the Dashboard, Services, Hosts , or Alerts pages?Do you see the Ambari Views option?

Does the npuser account now appear to have some permissions in Ambari?

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Users and Groups

- 5 .  While logged in as npuser, select HDFS from the Services menu.

Are you able to view HDFS service information on the Summary page?

On the Summary page, do you see the Actions and Service Actions buttons?

Why?

Would this indicate that the npuser account now has operator permission?

- 6 .  Sign out of the npuser account.

- Result

- You have now:

- Connected to your lab environment; logged in and started your one-node HDP cluster; viewed Hadoop

- service accounts; used the Ambari Web UI to add user accounts; tested the functionality of the new

- user accounts you created; created a new Ambari user group and added accounts and permissions to

- it; and tested the interaction between user permissions and group persmissions.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Managing Hadoop Services

- About This Lab

- Objective:

To use the Ambari Web UI to manage Hadoop services

- File locations:

N/A

- Successful outcome:  You will: View the Hadoop service configuration files that were installed

with Ambari; tour Ambari Web UI service management and configurationfeatures; change the HDFS service configuration using the Ambari Web UI;create an Ambari Configuration Group; and download HDFS clientconfiguration files.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Managing Hadoop Services

- Viewing Hadoop Service Configuration Files

- View the Hadoop service configuration files that were installed by Ambari.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  List the core Hadoop service configuration files in the /etc/hadoop/conf directory on node1.

- # ls /etc/hadoop/conf

Notice specifically the core-site.xml, hadoop-site.xml, and mapred-site.xml files.These files are some of the more commonly updated Hadoop configuration files.

Do you see service configuration files for Hive, ZooKeeper, AMS (Ambari Metrics System),Ambari, or Tez? You should not.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 3 .  List the names of the configuration files for other common Hadoop services.

- # ls /etc/ambari-server/conf

- # ls /etc/ambari-agent/conf

- # ls /etc/hive/conf

- # ls /etc/pig/conf

- # ls /etc/zookeeper/conf

- 4 .  The next lab step will use the jar command to display the contents of a .jar file. The jar

command is not typically specified in the shell PATH environmental variables. To mitigate this,run the following command:

- # export PATH=$PATH:/usr/jdk64/jdk1.8.0_40/bin

- 5 .  Use the jar command to display the name of the hdfs-default.xml file, which is one of the

default configuration files installed as part of core Hadoop. The default files are typicallyinstalled as part of Java JAR files.

- # jar tvf /usr/hdp/2.3.0.0-2557/hadoop-hdfs/hadoop-hdfs.jar | grep xml

- Ambari Web UI Management and Configuration Features

- Tour the Ambari Web UI service management and configuration features.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Click Services in the Ambari Web UI.

The list of installed services appears on the left side of the Services page and includes suchservices has HDFS, MapReduce2, YARN, and others.

- 4 .  Click to open and view the Actions menu button below the list of installed cluster services.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Services

Notice that you can install and configure new cluster services, as well as

start or stop all currently installed cluster services.

To save time during this lab exercise, you will not take the 5-10 minutes

to stop and then start all cluster services.

- 5 .  Ensure that the HDFS service is selected on the Services page.

- 6 .  Click to open and view the Service Actions menu button in the top right-side corner of the

Services page.

Notice that the actions listed on the Service Actions menu button are specific to thecurrently selected service, in this case HDFS.

Many of the actions listed here are performed in this and other lab exercises.

- 7 .  With the HDFS service still selected, click Quick Links and select NameNode UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

The NameNode UI Web interface opens on another browser tab.

Not all services include their own Web interfaces, but if they do, they can be accessed from theAmbari Quick Links menu when that service is selected on the Services page.

The NameNode UI is described and used in another lesson.

- 8 .  Close the NameNode UI browser tab.

With the HDFS service still selected, view the types of information available on the Summarypage.

The types of information available will vary with each cluster’s specific configuration.

The partial screen capture below might be different from the HDFS information displayed foryour lab cluster.

- 9 .  With the HDFS service still selected, view the types of metric information available on the

Heatmaps page.

The types of information available will vary with each cluster’s specific configuration.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 10 . The partial screen capture below could be different from the HDFS information displayed for

your lab cluster.

- Changing HDFS Service Configuration

- Change the HDFS service configuration using the Ambari Web UI.

- 1 .  With the HDFS service still selected, click the Configs tab.

- 2 .  On the Settings page, scroll down to find and change the NameNode Java heap size

setting. Change it by dragging the slider bar to 4GB. Do not save the change.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 3 .  NOTE

This is not the size recommended by Ambari Guided Configuration for the current cluster, soyou will change this setting back in the next lab step.

- 4 .  Use Ambari Guided Configuration to return the NameNode Java heap size back to its

recommended setting.

Click the gray-colored, clock-wise circular arrow icon to have Guided Configuration return theheap size to the recommended value.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 5 .  With the HDFS service still selected, click the Advanced tab.

- 6 .  Scroll down to find and expand the Advanced hdfs-site section.

Scroll down to find the parameter dfs.replication.max and change it from 50 to 40, andthen click Save.

- 7 .  When asked to save the configuration, you can optionally enter Notes and then click Save

again.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 8 .  Then click OK in the confirmation window.

- 9 .  At the notification to restart HDFS (and MapReduce2 and YARN), click Restart and select

Restart All Affected.

- 10 . In the confirmation window, click Confirm Restart All.

A Background Operation Running window opens and displays the progress of the restart.Click OK to dismiss this window once HDFS has been restarted.

- 11 . Ambari displays a restart icon next to any other service or services that must also be restarted.

Select each service that Ambari indicates must be restarted and then follow the sameprocedure that you just used to restart HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 12 . Reselect the HDFS service and ensure that you have clicked its Configs tab.

You should now have a configuration change history for HDFS.

The version 1 configuration was the configuration created during installation.

The version 2 configuration includes the change to the dfs.replication.max parameter.- 13 . Float the mouse pointer over the V1 configuration and select Compare in the pop-up window.

This enables you to compare the change between the V1 and the current (V2) HDFS

configuration.

The current configuration is indicated by the green check box.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 14 . Float the mouse pointer over the V1 configuration and select Make Current in the pop-up

window.

This enables you to revert to the V1 HDFS configuration.

Click Make Current again when the confirmation window opens.

- 15 . Ambari displays a restart icon next to any service or services that must also be restarted as a

result of the HDFS configuration change.

Select each service indicated by Ambari and restart it.

- Creating an Ambari Configuration Group

- Create an Ambari Configuration Group.

- 1 .  Select the HDFS service and click its Configs tab.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 2 .  Click Manage Config Groups.

Notice the name of the currently selected configuration group.

It is HDFS Default and has one cluster node assigned to it.

Any configuration change that is made will be made to this configuration group and applied tothe single cluster node that is assigned to this configuration group.

- 3 .  In the Manage HDFS Configuration Groups window, click the + (plus icon) button beneath the

HDFS Default configuration group to create a new configuration group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 4 .  In the Create New Configuration Group window, type MoreDataNodeHeapSize

as the configuration group name and add an optional description.

Then click OK.

- 5 .  Normally you would then click the (+) plus icon on the right side of the window to add some

of the HDFS DataNodes to the configuration group.

However at this point in the lab configuration, there is only a single HDFS DataNode so you willskip this step.

Instead, just click Save to save the new configuration group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 6 .  With the HDFS service still selected, ensure that you are on the Settings tab

on the Configs page.

Scroll down, if necessary, to change the DataNode maximum Java heap size property to2GB.

Then use the green plus sign icon (the Override icon) to change this property setting for aspecific configuration group.

- 7 .  Select the configuration group created earlier (it is likely already selected).

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

Click OK.

- 8 .  In future labs when making modifications to HDFS, it is important to ensure

that the HDFS Default configuration group is selected rather than the new

MoreDataNodeHeapSize configuration group.

This will ensure that any HDFS modification will be made to the DataNode

that is assigned to the HDFS Default configuration group.

- Downloading HDFS Configuration Files

- Download HDFS client configuration files.

- 1 .  With the HDFS service still selected, click the Service Actions menu button and select

Download Client Configs.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Services

- 2 .  Choose Save File and click OK.

- 3 .  Open a new terminal window on your Ubuntu desktop and change directory to

/root/Downloads.

Then display the contents of the Downloads directory using the ls command.

- 4 .  Uncompress and untar the file using the tar xvfz HDFS_CLIENT-configs.tar.gz command.

Notice the names of the HDFS client configuration files.

Each service or application has its own set of configuration files.

- 5 .  Close the terminal window on the Ubuntu desktop when you are finished.

- Result

- You have now:

- Viewed the Hadoop service configuration files that were installed with Ambari; toured Ambari Web UI

- service management and configuration features; changed the HDFS service configuration using the

- Ambari Web UI; create an Ambari Configuration Group; and downloaded HDFS client configuration

- files.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

- Lab: Using Hadoop Storage

- About This Lab

- Objective:

To view and manage HDFS files and directories using the HDFS Shell, theAmbari Files View and the NameNode UI

- File locations:

N/A

- Successful outcome:

You will: Explore the HDFS Shell; use the HDFS Shell to manage filesand directories in HDFS; use HDFS Shell command-line options tooverride the cluster's default HDFS properties; configure the Ambari FilesView; and use the NameNodeUI file browser to view files and directories.- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Using Hadoop Storage

- Exploring HDFS Shell

- Learn to use the HDFS Shell.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Display usage information for the HDFS Shell.

- # hdfs dfs

- 3 .  Display the online manual help for the HDFS Shell.

- # hdfs dfs -help

- 4 .  Display the online manual help for a specific HDFS Shell command.

- # hdfs dfs -help ls

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 5 .  Use the HDFS Shell to list files and directories on the local file system.

- # hdfs dfs -ls file:///usr

- 6 .  Use the HDFS Shell to list files and directories in HDFS.

- # hdfs dfs -ls hdfs:///user

- # hdfs dfs -ls /user

Notice that the last two commands list the same HDFS files and directories,

but the format of the command output is slightly different

- Using the HDFS Shell

- Use the HDFS Shell to manage files and directories in HDFS.

- 1 .  List files and directories in the HDFS root (/) directory.

- # hdfs dfs -ls /

You should see a list of directory names.

- 2 .  List the root user’s HDFS home directory by issuing the same command again,

but this time without supplying a directory path argument.

- # hdfs dfs -ls

The command fails because the root user does not have an HDFS home directory.

- 3 .  Create an HDFS home directory for the root user.

- # hdfs dfs -mkdir /user/root

The command fails because the root user does not have HDFS permissions to write to the/user directory.

- 4 .  View the name of the user that has superuser privileges in HDFS.

- # more /etc/hadoop/conf/hdfs-site.xml

Search for the dfs.cluster.administrators property.

Which user is an HDFS superuser?

- 5 .  Switch to the HDFS superuser account and create the root user’s home directory using the

command sequence shown below.

- # su - hdfs

- $ hdfs dfs -mkdir /user/root

- $ hdfs dfs -ls /user

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using Hadoop Storage

Notice that the directory owner and group owner are both hdfs and should be root.

Use the HDFS Shell –chown command to change the directory’s ownership.

- $ hdfs dfs -chown root:root /user/root

- $ hdfs dfs -ls /user

Notice that the directory owner and group owner are now root.

Now use the exit command to switch back to normal root user account permissions.

- $ exit

- 6 .  List the root user’s HDFS home directory.

- # hdfs dfs -ls

Although the command should execute properly, there are no files or directories to list in theroot user’s HDFS home directory.

- 7 .  Create a subdirectory hierarchy in the root user’s HDFS home directory.

- # hdfs dfs -mkdir -p dir1/dir2/dir3

- 8 .  Recursively list the contents of the root user’s HDFS home directory to verify that the

directory hierarchy was created.

- # hdfs dfs -ls -R

- 9 .

Copy the file /root/labs/constitution.txt from the local file system to the root user’sHDFS home directory.

Then list the root user’s HDFS home directory to verify that the file was copied.

- # hdfs dfs -put /root/labs/constitution.txt constitution.txt

- # hdfs dfs -ls

- 10 . Display the contents of the constitution.txt file in the root user’s HDFS home directory.

- # hdfs dfs -cat constitution.txt | more

- 11 . View only the last 1 KB of the constitution.txt file in the root user’s HDFS home directory.

- # hdfs dfs -tail constitution.txt

- 12 . Copy the constitution.txt file from the root user’s HDFS home directory to the root user’s

home directory in the local file system. Then list the root user’s home directory in the local filesystem to verify that the file was copied.

- # hdfs dfs -get constitution.txt /root/constitution.txt

- # ls /root

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 13 . Move the constitution.txt file in the root user’s HDFS home directory to the HDFS

directory   /user/root/dir1/dir2/dir3.

Then recursively list the root user’s HDFS home directory to verify that the file was moved.- # hdfs dfs -mv constitution.txt dir1/dir2/dir3

- # hdfs dfs -ls -R

- 14 . Copy the local files /etc/passwd and /etc/hosts to the root user’s HDFS home directory.

Then copy these two files back to the root user’s home directory on the local file system,ensuring that during the copy process the files are merged into a single file named

passwd_hosts.

Then view the contents of the merged file to verify that the process properly completed.- # hdfs dfs -put /etc/passwd passwd

- # hdfs dfs -put /etc/hosts hosts

- # hdfs dfs -ls

- # hdfs dfs -getmerge passwd hosts /root/passwd_hosts

- # cat /root/passwd_hosts

- 15 . Remove the passwd file from the root user’s HDFS home directory.

Then list the HDFS home directory to verify that it has been removed.

- # hdfs dfs -rm passwd

- # hdfs dfs -ls

What message did you receive when you removed the passwd file?

When you listed the contents of the HDFS home directory, did you notice the new .Trashdirectory?

- 16 . Recursively list the contents of the root user’s HDFS .Trash directory.

- # hdfs dfs -ls -R .Trash

Was the passwd file completely removed, or was it temporarily moved to the HDFS .Trashdirectory?

- 17 . Retrieve the passwd file from the HDFS .Trash directory by moving it back to the root user’s

HDFS home directory.

Once finished, recursively list the contents of the HDFS home directory to verify that theoperation completed successfully.

- # hdfs dfs -mv .Trash/Current/user/root/passwd passwd

- # hdfs dfs -ls -R

- 18 . View the contents of the HDFS /user/root/dir1/dir2/dir3 directory and then remove the

dir3 directory.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using Hadoop Storage

Then verify that the dir3 directory and its files were removed.

- # hdfs dfs -ls dir1/dir2/dir3

- # hdfs dfs -rm dir1/dir2/dir3

What message did you receive?

The –rm command (with no other command options) cannot remove directories.

- 19 . Try to remove the dir3 directory again, but this time include the –rm command’s –R option.

List the contents of the dir2 directory to verify that the dir3 directory was removed.

- # hdfs dfs -rm -R dir1/dir2/dir3

- # hdfs dfs -ls dir1/dir2

Was the directory removed?

It should be.

- Overriding Default HDFS Properties

- Use HDFS Shell command-line options to override the cluster’s default HDFS

- properties.

- 1 .  View the default HDFS block size as defined by the dfs.blocksize property in the

/etc/hadoop/conf/hdfs-site.xml file.

- # more /etc/hadoop/conf/hdfs-site.xml

It should be 134,217,728 bytes (128 MB).

- 2 .  Write the /root/data/test_data file to the root user’s HDFS home directory using the non-

default  block size of 1,000,000 bytes.

- # hdfs dfs -D dfs.blocksize=1000000 -put /root/data/test_data test_data

The command should fail with a message reporting the reason for the failure.

The minimum block size must be at least 1,048,576 bytes based on the

dfs.namenode.fs-limits.min-block-size property defined in the hdfs-default.xmlfile.

- 3 .  Write the /root/data/test_data file to the root user’s HDFS home directory using the

non-default block size of 1,050,000 bytes, which is larger than the minimum block size.- # hdfs dfs -D dfs.blocksize=1050000 -put /root/data/test_data test_data

The command should fail with a message reporting the reason for the failure.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using Hadoop Storage

While the minimum block size has been met, the block size must also be a multiple of 512bytes in order to support the checksum system used to verify HDFS data integrity.  This isbased on the dfs.bytes-per-checksum property defined in the hdfs-default.xml file.- 4 .  Write the /root/data/test_data file to the root user’s HDFS home directory using the

non-default block size of 1,049,088 bytes.

- # hdfs dfs -D dfs.blocksize=1049088 -put /root/data/test_data test_data

The command should have completed successfully as the block size of 1,049,088 bytes isexactly the

minimum required block size plus an additional 512 bytes.

- Configuring Ambari Files View

- Configuring Ambari Files View

- Configure the Ambari Files View

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server

at the URL http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 4 .  Click Configs and then click the Advanced tab.

Also ensure that the HDFS Default configuration group is selected.

- 5 .  Scroll down to find and expand the Custom core-site section and then click Add Property.

- 6 .  Click the double-tag icon and then add the property and value

hadoop.proxyuser.root.groups=* and the property and

value hadoop.proxyuser.root.hosts=* to the Custom core-site section.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using Hadoop Storage

Then click Add.

- 7 .  Click Save to save the modifications.

Click Save again in the Save Configuration window.

Click OK in the confirmation window.

- 8 .  Restart any services as indicated in the Ambari Web UI.

- 9 .  Select Manage Ambari from the admin menu button in order to start the process of creating

an instance of an Ambari View.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 10 . Click Views.

- 11 . Click to expand Files and then click Create Instance.

- 12 . In the Details section, enter FileView1_0 as the Instance Name,

My HDFS Files as the Display Name,

and Browse my HDFS files and directories as the Description.

Then scroll down and click Save.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 13 . Scroll down and locate the Permissions section.

Beneath Grant permissions to these users, then click New and type admin.

Click the blue check box to save your change.

- 14 . In a terminal window logged in to node1, create the HDFS home directory /user/admin for the

admin user account.

You will need HDFS superuser privilege to create this home directory.

- # su - hdfs

- $ hdfs dfs -mkdir /user/admin

- $ hdfs dfs -chown admin:admin /user/admin

- $ exit

- 15 . Back in the Ambari Web UI,

click the Views icon and select the View named My HDFS Files.

- 16 . You will be taken to the / directory of HDFS, however the admin user does not have sufficient

HDFS permissions to do anything here but view the directory names.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using Hadoop Storage

Notice that the New directory and Upload buttons are not activated due to the lack ofnecessary HDFS permissions.

- 17 . Browse to the /user/admin directory by clicking on the user folder link at

the bottom of the menu.

Next click the admin folder link.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Using Hadoop Storage

You will know you are in the proper place when the New directory and Upload buttons attop-right are activated.

A closer look:

- 18 . Click New directory to create a new HDFS directory in the admin user’s HDFS home

directory.

- 19 . Name the new directory dir1 and then click Create.

- 20 . Click dir1 to open the dir1 directory.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im5](images/Im5)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 21 . Click Upload to upload a file to the dir1 directory.

- 22 . Click Browse and in the file browser window, browse to File System,

then etc, select  passwd, and then click Open.

Once the passwd file has been selected, click Upload.

The result should look like the following:

- Using the NameNode UI File Browser

- Use the NameNode UI file browser to view HDFS files and directories.

- 1 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 2 .  On the Summary page, click Quick Links and select NameNode UI.

- 3 .  In the Firefox browser, click the new Namenode information tab, if necessary, to move to

the NameNode UI.

- 4 .  In the NameNode UI, click Utilities and select Browse the file system.

- 5 .  To view the contents of the /user/admin/dir1 directory, click the user directory name.

Then click the admin directory name followed by the dir1 directory name.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im5](images/Im5)

![Im6](images/Im6)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 6 .  To view information about the passwd file in HDFS, click the passwd file name.

Notice that the only way to view the file contents is to download the file to the local machine.This could be a lengthy or even impossible process for the large files often stored in HDFS.- 7 .  Click Close to close the open File information window.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using Hadoop Storage

- 8 .  You can also easily view directory contents or file information if you know the name and path to

a file or directory.

In the NameNode UI on the Browse Directory page, type /user/root into the path nametext box and then press the Return key.

- 9 .  Close the NameNode UI browser tab when you are finished with the NameNode UI.

- Result

- You have now:

- Explored the HDFS Shell; used the HDFS Shell to manage files and directories in HDFS; used HDFS

- Shell command-line options to override the cluster's default HDFS properties; configured the Ambari

- Files View; and used the NameNodeUI file browser to view files and directories.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Using WebHDFS

- About This Lab

- Objective:

To gain familiarity with some basic operation of WebHDFS

- File locations:

N/A

- Successful outcome:

You will: Use Ambari Web UI to verify that WebHDFS is enabled in yourcluster and used WebHDFS API commands to create an HDFS directory,list an HDFS directory, and read a file from HDFS.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Using Hadoop Storage

- Verifying WebHDFS is Enabled

- Use the Ambari Web UI to verify that WebHDFS is enabled in your cluster.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server

at the URL http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using WebHDFS

- 4 .  Click Configs and then click the Advanced tab.

Ensure that the HFDS Default configuration group is selected.

- 5 .  Scroll down to find and expand the General section and look for the

WebHDFS enabled check box.

It should already be selected.

- 6 .  You are finished using the Ambari Web UI.

- Using WebHDFS API Commands

- Use WebHDFS API commands as arguments to the Linux curl command.

- (This can be useful to ensure that WebHDFS is functioning properly.)

- 1   Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Using WebHDFS

- 2   Use the curl command with WebHDFS API arguments to list the contents

of the HDFS /user/root directory.

- # curl -i “http://node1:50070/webhdfs/v1/user/root?op=LISTSTATUS”

You should see a 200 OK response (you might have to scroll up in the terminal window), alongwith a JSON object containing the list of files and directories in the /user/root directory.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Using WebHDFS

- 3   Create a new subdirectory named history in /user/root.

The following command is entered on a single line.

- # curl -i X PUT

- “http://node1:50070/webhdfs/v1/user/root/history?op=MKDIRS&user.name=root”

The user.name=root argument is required to have the necessary permissions to write to the/user/root directory.

- 4   Use the HDFS Shell –ls command to verify that the history subdirectory was

created successfully.

- # hdfs dfs -ls

You should see a history directory in the output.

- 5   Read the contents of the passwd file using the following

curl command and WebHDFS API.

- # curl -i -L “http://node1:50070/webhdfs/v1/user/root/passwd?op=OPEN”

The contents of the file may scroll out of the terminal window.

- Result

- You have now:

- Used Ambari Web UI to verify that WebHDFS is enabled in your cluster and used WebHDFS API

- commands to create an HDFS directory, list an HDFS directory, and read a file from HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Using HDFS Access Control Lists

- About This Lab

- Objective:

To configure and use HDFS access control lists (ACLs)

- File locations:

N/A

- Successful outcome:  You will: Configure HDFS ACL support; create and manage file ACL

entries, manage ACL entries and default ACL entries on directories; andmanage user and group access using an access mask.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Using Hadoop Storage

- Configuring HDFS ACLs

- Use the Ambari Web UI to configure HDFS access control list support.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server

at the URL http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 4 .  Click Configs and then click the Advanced tab.

Ensure that the HDFS Default configuration group is selected.

- 5 .  Scroll down to find and expand the Custom hdfs-site section.

Click Add Property.

- 6 .  Click on the single-tag button, and then add the dfs.namenode.acls.enabled property with

a value of true.

Click Add.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 7 .  Click Save to save your changes.

- 8 .  Restart any services as indicated in the Ambari Web UI.

HDFS access control support has now been enabled.

- Managing File ACLs

- Create and Manage File ACL entries.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Then use SSH to log in to node1.

- # ssh node1

- 2 .  Create a test directory named /acltests.

All testing of HDFS ACLs will occur in this directory.

You must become the HDFS superuser to configure the test environment.

- # su - hdfs

- $ hdfs dfs -mkdir /acltests

- $ hdfs dfs -ls /

Notice that:

- the directory owner is hdfs,

- the group is hdfs,

- the directory grants read and execute access to anyone who is not the hdfs user or belongsto the hdfs group.

For example, the root user could access files in the /acltests directory.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 3 .  In order to have a file for test purposes, upload a copy of the local file /etc/passwd to the

HDFS /acltests directory.

Verify that the file was uploaded.

- $ hdfs dfs -put /etc/passwd /acltests

- $ hdfs dfs -ls /acltests

Notice that:

- the file owner is hdfs,

- the group is hdfs,

- the file grants read access by anyone who is not the hdfs user or does not belong to the hdfsgroup.

- 4 .  Remove read permissions from the /acltests/passwd file for anyone who is not hdfs or does

not belong to the hdfs group.

- $ hdfs dfs -chmod 640 /acltests/passwd

- $ hdfs dfs -ls /acltests

The file permissions should now be rw-r-----.

For example, the root user should not be able to read the passwd file.

- 5 .  To test root user read access to the /acltests/passwd file, assume normal root permissions

again.

Then try to read the file.

- $ exit

- # hdfs dfs -cat /acltests/passwd

The –cat command should have failed with a message providing information about why thecommand failed.

- 6 .  To continue the testing, assume HDFS superuser privileges again.

- # su - hdfs

- 7 .  Use the HDFS Shell –getfacl command to view any ACL entries that might exist on the

/acltests/passwd file.

- $ hdfs dfs -getfacl /acltests/passwd

There should be no ACL entries on the file.

It should have only standard HDFS user, group, and other permissions.

- 8 .  Use the HDFS Shell –ls command on the /acltests directory.

- $ hdfs dfs -ls /acltests

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

Any file or directory with an ACL entry has a + character appended to the end of the

permissions list.

Is there a + character for the passwd file?

There should not be.

- 9 .  Use the HDFS Shell –setfacl command to add an ACL entry for the root

user that provides read access to the /acltests/passwd file.

Then use the HDFS Shell  –getfacl command to verify the change.

- $ hdfs dfs -setfacl -m user:root:r-- /acltests/passwd

- $ hdfs dfs -getfacl /acltests/passwd

You should see a new ACL entry for user:root:r--.

You should also see a new mask::r-- entry.

- 10 . Use the HDFS Shell –ls command on the /acltests directory.

- $ hdfs dfs -ls /acltests

Any file or directory with an ACL entry has a + character appended to the end

of the permissions list.

Is there a + character for the passwd file?

There should be.

- 11 . To test root user read access, assume normal root permissions again.

- $ exit

- 12 . Use the HDFS Shell –cat command to try to read the /acltests/passwd file.

- # hdfs dfs -cat /acltests/passwd

You should be able to view the contents of the file.

- 13 . Assume HDFS superuser permissions again.

- # su - hdfs

- 14 . Add another ACL entry to the /acltests/passwd file.

This time provide the group hcat read and write access to the file.

Verify the change once you have added the new ACL entry.

- $ hdfs dfs -setfacl -m group:hcat:rw- /acltests/passwd

- $ hdfs dfs -getfacl /acltests/passwd

You should see a new ACL entry for group:hcat:rw-.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 15 . Remove the ACL entry for the group hcat from the /acltests/passwd file.

Verify the change once you have removed the ACL entry.

- $ hdfs dfs -setfacl -x group:hcat /acltests/passwd

- $ hdfs dfs -getfacl /acltests/passwd

Only the ACL entry for group:hcat:rw- should have been removed.

- 16 . Use the HDFS Shell –setfacl command with the --set option to completely remove and replace

the entire set of ACL entries.

Verify the change once you have finished.

- $ hdfs dfs -setfacl --set user::rw-,group::rw-,other::---,user:admin:rw-

- ,group:hcat:rw- /acltests/passwd

- $ hdfs dfs -getfacl /acltests/passwd

You should see the entire set of permissions and ACL entries replaced with the permissionsand ACL entries specified in the command.

For example, there should no longer be an ACL entry for user:root:r--.

- 17 . Remove all ACL entries from the /acltests/passwd file.

Verify the removal when you have finished.

- $ hdfs dfs -setfacl -b /acltests/passwd

- $ hdfs dfs -getfacl /acltests/passwd

Only standard HDFS user, group, and other permissions should remain.

- 18 . Upload the /etc/group file from the local file system to the HDFS /acltests directory. This

file will be referenced in the next lab section.

- $ hdfs dfs -put /etc/group /acltests/group

- $ hdfs dfs -ls /acltests/

- Managing Directory ACLs

- Manage ACL entries and default ACL entries on directories.

- 1 .  While you still have HDFS superuser priveleges, check whether there are ACL entries for the

/acltests directory.

- $ hdfs dfs -getfacl /acltests

- $ hdfs dfs -ls /

Both commands should reveal that the directory does not have ACL entries.

(Remember that the HDFS Shell –ls command displays a + character at the end of thepermissions list for any file or directory that has ACL entries.)

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 2 .  Add a default ACL entry for the root user to the /acltest directory.

The default ACL entry should provide the root user with read and write permissions.

Verify the changes once you have finished.

- $ hdfs dfs -setfacl -m default:user:root:rw- /acltests

- $ hdfs dfs -getfacl /acltests

Is there a default ACL entry for default:user:root:rw-?

There should be.

There should also be default entries for user, group, mask, and other too.

The entries for user, group, and other were automatically created based on the HDFSpermissions for user, group, and other.

The mask was automatically created based on the union of the user:root:rw- and

group::r-x permissions.

- 3 .  Upload a copy of the local file /etc/hosts to the HDFS /acltests directory.

Verify that the file was uploaded.

- $ hdfs dfs -put /etc/hosts /acltests

- $ hdfs dfs -getfacl /acltests/hosts

Did the file inherit the ACL user:root:rw- from the parent directory’s default ACL entries?It should have.

Look at the mask:: that was calculated for the file. Does this access mask limit the effectivepermissions of any users or groups?

It should.

- 4 .  View the ACL entries for the /acltests/group file.

- $ hdfs dfs -getfacl /acltests/group

Is there an ACL entry for user:root:rw-?

There should not be.

Default ACL entries on a directory only affect files that are added to the directory after thedefault ACL entries are created.

The group file was created in the directory before the default ACL entries were created.- 5 .  To test root user read access to the hosts file, assume normal root permissions again.

- $ exit

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

- 6 .  Use the HDFS Shell –cat command to try to read the /acltests/hosts file.

- # hdfs dfs -cat /acltests/hosts

You should be able to read the hosts file as the root user.

- 7 .  Assume HDFS superuser permissions again.

- # su - hdfs

- 8 .  Create a dir1 subdirectory in the /acltests directory.

Verify that it was created in the correct location.

- $ hdfs dfs -mkdir /acltests/dir1

- $ hdfs dfs -ls /acltests

You should see the dir1 directory listed.

Does the HDFS Shell –ls command output indicate that dir1 has ACL entries?

Do you see a + character?

You should have.

- 9 .  Display the ACL entries for the dir1 directory.

- $ hdfs dfs -getfacl /acltests/dir1

Do you see an ACL entry for user:root:rw-?

You should.

Do you see a list of default ACL entries?

You should.

Any files created in dir1 will inherit its ACL entries.

Any directories created in dir1 will inherit not only its ACL entries, but also its default ACLentries.

- Managing Access Using an Access Mask

- Manage user and group access using the access mask.

- 1 .  While you still have HDFS superuser permissions, change the access mask for

/acltests/hosts so that the unnamed group or any specific user or groups cannot read thehosts file.

Verify the change once you have finished.

- $ hdfs dfs -setfacl -m mask::--- /acltests/hosts

- $ hdfs dfs -getfacl /acltests/hosts

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using HDFS Access Control Lists

What are the effective permissions for user:root: and group::?

There should be no effective permissions.

- 2 .  To test root user read access to the hosts file, assume normal root permissions again.

- $ exit

- 3 .  As the root user, try to read the /acltests/hosts file.

- # hdfs dfs -cat /acltests/hosts

Were you able to read the file?

You should not have been able to.

- Result

- You have now:

- Configured HDFS ACL support; created and managed file ACL entries, managed ACL entries and

- default ACL entries on directories; and managed user and group access using an access mask.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Managing Hadoop Storage

- About This Lab

- Objective:

To manage and monitor HDFS storage using the Ambari Web UI,NameNode UI, DataNode UI, and HDFS command-line commands- File locations:

N/A

- Successful outcome:

You will: View and manage Ambari Web UI HDFS monitoring widgets;manage and monitor HDFS services and storage using the NameNode UIand command-line commands; check HDFS file system consistency usingthe fsck command; and view a DataNode block scanner report.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Managing Hadoop Storage

- Managing and Monitoring with Ambari

- View, monitor, and manage the HDFS service and HDFS storage using the Ambari Web

- UI and NameNode UI.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at

the URL http://node1:8080.

Log in to the Ambari Web UI using the user name admin and the password admin.

- 2 .

- 3 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 4 .  Click to open and view the Service Actions menu button in the top right-side corner of the

Services page.

Notice that the actions listed on the Service Actions menu button are specific to thecurrently selected

service, in this case HDFS.

Many of the actions listed here are performed other lab exercises.

With Services and HDFS still selected, click Configs and then the Advanced tab.

Ensure that the HDFS Default configuration group is selected.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 5 .  Scroll down to the General section.

Change the minimum Block replication from 3 to 1.

This change means that HDFS will only require one copy of each data block on the system.NOTE

This change is not retroactive to existing data blocks. It only affects new data blocks writtenafter this change has been made.

While this setting is not as safe as maintaining three copies of each data block, it does matchthe current HDFS cluster configuration because there is only a single DataNode at this time.(More DataNodes will be added in another lab and the replication factor will be configured to aminimum of three.)

- 6 .  Click Save to save your change.

Then click Save to confirm the change.

Click OK to dismiss the progress window.

- 7 .  After the configuration change, restart any affected services as indicated in the Ambari Web UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 8 .  Open a terminal window on the Ubuntu desktop and use SSH to connect to node1.

View the replication factor for the existing files in the root user’s HDFS home directory.- # ssh node1

- # hdfs dfs -ls /user/root

The replication factor for the existing files should be three.

Directory names are not replicated.

- 9 .  The replication factor of an existing file can be changed.

Use the HDFS Shell –setrep command to change the /user/root/hosts file’s replicationfactor from three to one.

Verify the change once you are finished.

- # hdfs dfs -setrep -w 1 /user/root/hosts

- # hdfs dfs -ls /user/root

The replication factor of the hosts file should be one.

NOTE

Do not increase the replication factor beyond the current number of DataNodes.  A DataNodeis not allowed to maintain two copies of the same data block so the HDFS Shell

–setrep –w <n> command will not operate properly if the number of replicas exceeds thenumber of DataNodes.

- 10 . Go back to the Ambari Web UI.

With Services and HDFS selected, ensure that you are on the Summary page.

Scroll down to the Metrics section.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

Notice the types of HDFS metrics that are available.

Notice the Under Replicated Blocks widget. Even though the minimum replication factorwas reduced to one, there are HDFS files that were created before the replication factor wasreduced and those files are configured with a replication factor of three. These data blocks arereported as under replicated. Changing the default HDFS replication factor is not retroactive toexisting files and their data blocks.

- 11 . Float the mouse pointer over different widgets to view types of information that are displayed.

- 12 . In the Metrics section, click the Actions menu button.

Select Browse Widgets.

- 13 . On the HDFS tab, click Add to add the NameNode Operations widget.

Then click Close.

- 14 . Verify that the NameNode Operation widget is displayed in the Metrics section.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 15 . Float the mouse pointer over the NameNode Operations widget.

Notice and click the circled X icon to delete the widget from the Metrics section.

The widget should have been removed.

- 16 . Click the Last 1 hour menu button and notice the available list of time periods.

The name of the menu button will change depending on which option is currently selected.- 17 . With Services and HDFS selected, click Quick Links at the top of the page and then select

NameNode UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 18 . Using the information displayed in the NameNode UI, answer the following questions:

What date and time was HDFS last started?

Is safemode on or off?

What percentage of your HDFS (DFS) is used?

How many under-replicated blocks are there?

Why are many of the data blocks under replicated?

(Hint, there is only one DataNode right now and initially the minimum replication factor wasthree.)

What directory path on the NameNode holds the fsimage and edits files?

(it is called the NameNode Storage directory in the NameNode UI)

What is the name of the fsimage file that was used the last time HDFS was started?

- Managing and Monitoring with Commands

- Manage and monitor the HDFS service and HDFS storage using HDFS command-line

- commands.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Use the dfsadmin command to generate an HDFS report.

- # hdfs dfsadmin -report

Did the command work? Why not?

- 3 .  Assume HDFS superuser permissions and try to generate a dfsadmin report again.

- # su - hdfs

- $ hdfs dfsadmin -report

Did it work this time?

It should have.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 4 .  Using the dfsadmin report output, answer the following questions:

How much HDFS storage space is configured?

How much HDFS storage space is still available?

How many under-replicated block are there?

How many live DataNodes are there?

Does the dfsadmin -report command provide some of the same information as the NameNodeUI?

- 5 .  Assume normal root user privileges again.

- $ exit

- 6 .  Use the HDFS Shell –du (disk usage) command to view HDFS storage usage.

- # hdfs dfs -du /

Did the command fail?

It should have.

- 7 .  Run the HDFS Shell –du command again, but examine only the HDFS /user/root directory.

- # hdfs dfs -du /user/root

Did the command work this time?

It should have because the root user has the necessary HDFS permissions on its own homedirectory.

- 8 .  Run the HDFS Shell –du command again, but add the summary and human-readable command

options.

Note the effect on the displayed output.

- # hdfs dfs -du -h /user/root

- # hdfs dfs -du -s /user/root

- # hdfs dfs -du -h -s /user/root

- 9 .  Run the HDFS Shell –df (display file system) command.

- # hdfs dfs -df

What percentage of the available HDFS storage space has been used?

- 10 . Run the HDFS Shell –df command again but add the –h human-readable command option.

Note the effect on the displayed output.

- # hdfs dfs -df -h

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- Checking HDFS Consistency

- Check HDFS file system consistency.

- 1 .  Run the fsck command on the HDFS / directory.

- # hdfs fsck /

Did it work?

Why not?

- 2 .  Assume HDFS superuser permissions and try to run the fsck command again.

- # su - hdfs

- $  hdfs fsck /

Did it work this time?

It should have.

- 3 .  Assume normal root user privileges again.

- $ exit

- 4 .  Upload the local file /root/labs/hbase.jar to the root user’s HDFS home directory and

then verify that it was uploaded.

- # hdfs dfs -put /root/labs/hbase.jar /user/root

- # hdfs dfs -ls /user/root

- 5 .  Run the fsck command again, but run it only on the /user/root/hbase.jar file.

- # hdfs fsck /user/root/hbase.jar

View the command output and answer the following questions:

What are the total number of blocks in the file?

It should be one.

What is the default replication factor for this file?

It should be one.

Are there any under-replicated blocks for this file?

There should not be because the hbase.jar file was created after the default

replication factor was changed to one.

- 6 .  Examine the differences in the displayed output when using different combinations of fsck

command options. Run the fsck command again on the /user/root/hbase.jar file, but thistime add the –files option.

- # hdfs fsck /user/root/hbase.jar -files

Was the file name added near the beginning of the command output?

The answer should be yes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 7 .  Run the same command again but this time add the –files –blocks options.

- # hdfs fsck /user/root/hbase.jar -files -blocks

What was added to the information displayed by the command?

Do you see a block number?

You should. (It is prefaced by blk_.)

- 8 .  Run the same command again but this time add the –files –blocks -locations options.

- # hdfs fsck /user/root/hbase.jar -files -blocks -locations

What was added to the information displayed by the command?

Following the block number information do you a DataNode IP address and port number insidesquare brackets?

You should.

NOTE

This information is less interesting at this point in the lab configuration because there is only asingle DataNode. However, in a real-world cluster there are likely to be multiple DataNodelocations listed. With a replication factor of three and multiple DataNodes, you would see threeblocks with the same block ID number,

but on three different DataNodes.

- 9 .  Use the Linux find command to find the local file system file that contains the HDFS data block.

Use the example syntax below but substitute your actual block number as seen in the output ofthe previous fsck command.

- # find / -name ‘blk_107374XXXX’

Note the path to the data block. Does it begin with the path /hadoop/hdfs/data?

It should.

- 10 . The HDFS property dfs.datanode.data.dir contains one or more local file system paths

that are the parent

directories of the files containing the HDFS data blocks. Find and view the

dfs.datanode.data.dir property in the /etc/hadoop/conf/hdfs-site.xml file.- # more /etc/hadoop/conf/hdfs-site.xml

Does the path name in the property match the beginning of the path name you saw in theprevious lab step?

It should.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- Viewing a Block Scanner Report

- View a DataNode block scanner report.

- 1 .  Open a new tab in the Firefox browser on the Ubuntu desktop and type the following URL:

- http://node1:50075/blockScannerReport

How many blocks were scanned in the current period?

It might be zero.

If there is not any activity recorded, you might need to determine if the block scanner isenabled.

- 2 .  To determine if the block scanner is enabled, search the /etc/hadoop/conf/hdfs-

site.xml file for

the dfs.datanode.scan.period.hours property.

A negative value means that the block scanner is disabled while a positive value means that itis enabled.

- # more /etc/hadoop/conf/hdfs-site.xml

Did you find the property?

You should not have.

This means that the property has been set in the hdfs-default.xml file that is normallypackaged as part of a JAR file.

To find the default value of an HDFS property you will need to know the version of HDFS that isin use in your cluster.

One way to find your HDFS version number is to use the the Ambari Web UI to access theNameNode UI by

selecting Services > HDFS > Summary > Quick Links > NameNode UI.

The HDFS version is displayed on the NameNode UI Overview tab.

In this example the version number is 2.7.1.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Hadoop Storage

- 3 .  Use a Web browser to view the default value of an HDFS property by viewing the Apache

documentation

for the hdfs-default.xml file. You can perform a Google search for hdfs-default.xml butmany of the Google links might not point to the version of the file that matches your version ofHDFS. Examine any URL returned by Google and modify the version number within that URL, ifnecessary, to match your HDFS version. For example, the following URL displays the hdfs-default.xml property settings for HDFS version 2.7.1.

- http://hadoop.apache.org/docs/2.7.1/hadoop-project-dist/hadoop-hdfs/hdfs-

- default.xml

In the 2.7.1 version of the hdfs-default.xml file, the default value for the

dfs.datanode.scan.period.hours property is 504 hours, or 3 weeks. So the blockscanner is enabled but might not have performed any scanning yet.

- Result

- You have now:

- Viewed and managed Ambari Web UI HDFS monitoring widgets; managed and monitored HDFS

- services and storage using the NameNode UI and command-line commands; checked HDFS file

- system consistency using the fsck command; and viewed a DataNode block scanner report.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Managing HDFS Quotas

- About This Lab

- Objective:

To configure, test, and monitor HDFS storage name and space quotas- File locations:

N/A

- Successful outcome:  You will: Create a directory, assign name and space quotas to it, and

upload multiple files to the directory until both the space and name quotasare exceeded.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Managing Hadoop Storage

- Creating a Directory

- Create a directory.

- 1   Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2   Assume HDFS superuser permissions.

HDFS superuser permissions are required to configure HDFS storage name and space quotas.- # su - hdfs

- 3   Use the HDFS Shell –mkdir command to create a directory to test name and space quotas.

Verify that the directory was created.

- $ hdfs dfs -mkdir /qtests

- $ hdfs dfs -ls /

You should see the /qtests directory listed.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing HDFS Quotas

- Assigning Quotas

- Assign name and space quotas to the newly created directory.

- 1   You will be using the root user account to test the HDFS name and space quotas.

Use the HDFS Shell –chown command to change the ownership of the HDFS /qtestsdirectory to the root user.

Verify the ownership change once you are finished.

- $ hdfs dfs -chown root:root /qtests

- $ hdfs dfs -ls /

Does the root user own the HDFS /qtests directory?

It should.

- 2   Use the dfsadmin –setQuota command to assign a name quota to the HDFS /qtests

directory.

Set the name quota to 4 for testing purposes.

- $ hdfs dfsadmin -setQuota 4 /qtests

- 3   Use the dfsadmin –setSpaceQuota command to assign a space quota

to the HDFS /qtests directory.

Set the space quota to 134352500 for testing purposes.

- $ hdfs dfsadmin -setSpaceQuota 134352500 /qtests

- 4   Display the current quotas and quota usage for the HDFS /qtests directory. (A wide terminal

window will make viewing command output easier.)

- $ hdfs dfs -count -v -q /qtests

Use the command output to answer the following questions:

Do you see a name quota limit of 4?

You should.

Did the directory name itself consume a part of the name quota?

It should have.

So you see a space quota of 134,352,500 bytes?

You should.

Did the directory name consume any of the space quota?

It should not have.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing HDFS Quotas

- Testing Quotas

- Upload multiple files to the directory until both the space and name quotas are

- exceeded.

- 1   Assume normal root user privileges again in order to test the name and space quotas.

- $ exit

- 2   Upload the local file /root/labs/constitution.txt to HDFS as /qtests/file1.

Verify the upload once you have finished.

- # hdfs dfs -put /root/labs/constitution.txt /qtests/file1

- # hdfs dfs -ls /qtests

- 3   Display the current quotas and quota usage for the HDFS /qtests directory.

- # hdfs dfs -count -v -q /qtests

Use the command output to answer the following questions:

What is the remaining name quota?

It should be 2.

What some of the space quota used?

It should be.

Is there at least enough space for a default data block of 128 MB (134,217,728)?

There should be.

This means that a file that is a default block size or less can still be written to the directory.- 4   Again, upload the local file /root/labs/constitution.txt to HDFS as /qtests/file2.

This file will consume less than a data block and should upload.

Verify the upload once you have finished.

- # hdfs dfs -put /root/labs/constitution.txt /qtests/file2

- # hdfs dfs -ls /qtests

- 5   Again, display the current quotas and quota usage for the HDFS /qtests directory.

- # hdfs dfs -count -v -q /qtests

Is there still at least enough space for a default data block of 128 MB (134,217,728)?

There should be. This means that a file that is a default block size or less can still be written tothe directory.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing HDFS Quotas

- 6   This time try to upload a file that will consume more space than is allowed by the space quota.

Upload the /root/data/test_data file as /qtests/file3.

- # hdfs dfs -put /root/data/test_data /qtests/file3

Did it fail?

It should have because the file upload exceeded the space quota.

- 7   Again, upload the local file /root/labs/constitution.txt to HDFS as /qtests/file3.

This file will consume less than a data block and should upload.

Verify the upload once you have finished.

- # hdfs dfs -put /root/labs/constitution.txt /qtests/file3

- # hdfs dfs -ls /qtests

Did it upload?

It should have.

- 8   Again, display the current quotas and quota usage for the HDFS /qtests directory.

- # hdfs dfs -count -v -q /qtests

How much of the name quota is remaining?

It should be zero which means that no more files or directories can be created in the HDFS/qtests directory.

- 9   Again, attempt to upload the local file /root/labs/constitution.txt to HDFS as

/qtests/file4.

- # hdfs dfs -put /root/labs/constitution.txt /qtests/file4

Did it upload?

It should have failed and displayed a message about exceeding the name quota.

- 10  Remember that the HDFS replication factor is currently set to one. The default replication

factor is normally three. For each file, these two additional data block replicas would consumesome of the available space quota.

- Result

- You have now:

- Created a directory, assigned name and space quotas to it, and uploaded multiple files to the directory

- until both the space and name quotas were exceeded.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Managing the YARN Service Using Ambari Web UI

- About This Lab

- Objective:

To Use the Ambari Web UI and the ResourceManager UI to view andmanage YARN status and configuration properties

- File locations:

N/A

- Successful outcome:

You will: Explore the Ambari Web UI service management andconfiguration features for YARN and change the YARN service

configuration using the Ambari Web UI.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

YARN Resource Management

- Exploring the Ambari Web UI

- Explore the Ambari Web UI service management and configuration features for YARN.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Click Services in the Ambari Web UI.

- 4 .   Select the YARN service on the Services page.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 5 .  Click to open and view the Service Actions menu in the top right-side corner of the

Services page.

From here you can perform YARN management tasks such as restart YARN, restart

NodeManagers, turn on maintenance mode, and download YARN client configuration files.- 6 .  Click Quick Links and select ResourceManager UI.

The ResourceManager UI Web interface opens on another browser tab.

NOTE:

Depending on your lab setup, the default URL to the ResourceManager UI may be blocked.This is an artifact of the lab environment, and not likely an issue you would experience in thereal world.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

If simply clicking the quick link fails to open the ResourceManager UI, replace the default URLin the browser tab with node1:8088.

- 7 .  Take a few moments to click on the links in the menu on the left and familiarize yourself with

the various pages and the information they provide. Answer the following questions:

Where can you find information regarding the current version, last restart, and current status ofthe ResourceManager, as well as the current version of Hadoop and the Cluster ID?

Where can you find information for a node, such as its rack location, current state, address,HTTP address, Hadoop software version, and available resources?

Where can you find a list of all jobs that have been submitted but have not yet been

accepted/approved to run?

Where can you find a list of all jobs that have been approved but are not yet running?

Where can you find information on a job that has failed?

Where can you find information on a job that has successfully finished?

Where can you find information on queues and the jobs that are using them?

- 8 .  Close the ResourceManager UI browser tab.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 9 .  With the YARN service still selected in the Ambari Web UI, view the types of information

available on the Summary page. Use this page to answer the following questions:

What is the current status of the ResourceManager?

How many NodeManagers have been configured, and how many are currently started?How long has it been since the last time the ResourceManager was restarted?

What percentage of ResourceManager Heap is being used?

How many applications have been submitted? How many are currently running? How manyhave completed? How many have failed?

How many queues have been configured?

What percentage of cluster memory is currently being utilized? What is the average and maxusage?

(Make sure you look at Cluster Memory and not just YARN application memory usage.)Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 10 . With the YARN service still selected, view the types of metric information available on the

Heatmaps page.

Note that the number of nodes is visually reflected, so a single node is just a single bar,whereas three nodes would be represented with three separate bars.

- 11 . Hover over a node representation to see a quick view of node information such as the

underlying operating system, IP address, resource utilization, rack location and installedcomponents.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 12 . Click the bar representing the node in Heatmaps to look at information for that node under

the Hosts tab in the Ambari Web UI.

- 13 . Click the browser back button to go back to the Heatmaps tab under YARN Services.

Then click the Select Metric button to view the available metrics that can be viewed.- 14 . Finally, at the bottom of the Heatmaps key, find the Maximum value in the text box.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

Change this from 100% to 50% and note what this does to the key values.

- 15 .   The values for what constitutes the top green range change from 0-20 to 0-10.

This feature allows an administrator to determine what constitutes green, yellow, and redcluster nodes from a resource perspective.

- 16 .   Change Maximum back to 100%.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- Changing YARN Service Configuration

- Change the YARN service configuration using the Ambari Web UI.

- 1 .  With the YARN service still selected, click the Configs tab.

- 2 .  On the Settings page, scroll down to find and change the Memory allocated for all YARN

containers on a node setting.  Change it by dragging the slider bar down slightly. Do notsave the change.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

NOTE:

This is not the size recommended by Ambari Guided Configuration for the current cluster, soyou will change this setting back in the next lab step.

Also note that changing the maximum node memory available for YARN also changed themaximum container size memory (the setting to the right).

- 3 .  Click the yellow, counter-clockwise circular arrow icon to undo the change.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 4 .  With the YARN service still selected, click the Advanced tab.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing the YARN Service Using Ambari Web UI

- 5 .  Scroll down to find and expand the Advanced yarn-site section.

At this point, make no changes. Simply take a moment and familiarize yourself with the settingsthat are available here.

- Result

- You have now:

- Explored Ambari Web UI service management and configuration features for YARN and changed the

- YARN service configuration using the Ambari Web UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Managing the YARN Service Using the CLI

- About This Lab

- Objective:

To use CLI commands and the YARN API to manage the YARN service- File locations:

N/A

- Successful outcome:

You will: Use CLI user and administrator commands and run severalsimple YARN API calls.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

YARN Resource Management

- YARN CLI User Commands

- Use YARN CLI commands useful to users of a Hadoop cluster.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Find out what version of Hadoop is running on the system.

- # yarn version

- 3 .  Find out what happens when the yarn application –list command is executed without

supplying any application types or states.

- # yarn application -list

Note that by default, only applications that are in the SUBMITTED, ACCEPTED, or

RUNNING state are listed.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using the CLI

- 4 .  Generate a list of all applications that are in the FINISHED state.

- # yarn application -list -appStates FINISHED

- 5 .  Generate a list of nodes running the NodeManager daemon.

- # yarn node -list

What command would filter the list of nodes by those in the DECOMMISSIONED state?Hint: Use yarn node -help.

- 6 .  Run the yarn logs command without an application ID (which will cause it to fail), and pipe the

resulting help information to the more application to read.

- # yarn logs | more

Scroll through the information, noting the options that can be applied with this command oncean application ID is provided, or simply press q to quit the more application.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing the YARN Service Using the CLI

- YARN CLI Administrator Commands

- Use YARN CLI commands useful to administrators of a Hadoop cluster.

- 1 .  Restart the YARN ResourceManager daemon on node1.

- # yarn resourcemanager

Restarting the ResourceManager daemon does not interrupt the uptime calculation for theResourceManager service. This can be verified by going to the YARN Services page in theAmbari Web UI after running the command above.

What is the command to restart the NodeManager daemon?

Hint: Use yarn -help.

- 2 .  Find out what log level the ResourceManager daemon is running at on node1.

- # yarn daemonlog -getlevel node1:8088 resourcemanager

- 3 .  Find out what groups the hdfs user belongs to.

- # yarn rmadmin -getGroups hdfs

- 4 .  The next command needs to be run as the built-in yarn user, so switch to that user before

moving on.

- # su yarn

- 5 .  Run the command that will refresh node information for the ResourceManager.

- $ yarn rmadmin -refreshNodes

- 6 .  Return to acting as the root user.

- $ exit

- YARN API Calls

- Run some simple YARN API calls using cURL.

- 1 .  Generate general cluster information such as the cluster ID and software version.

- # curl -X GET http://node1:8088/ws/v1/cluster/info

- 2 .  Generate cluster metrics information such as number of completed applications, resources

available, and decommissioned nodes.

- # curl -X GET http://node1:8088/ws/v1/cluster/metrics

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing the YARN Service Using the CLI

- 3 .  Generate cluster scheduler information such as queues, available capacity, and maximum

number of applications allowed.

- # curl -X GET http://node1:8088/ws/v1/cluster/scheduler

- 4 .  Generate information on cluster applications such as application ID and status.

- # curl -X GET http://node1:8088/ws/v1/cluster/apps

- 5 .  Generate cluster information on cluster nodes such as the host names, status, software

version, and available resources.

- # curl -X GET http://node1:8088/ws/v1/cluster/nodes

- 6 .  Generate general information about node1.

- # curl -X GET http://node1:8042/ws/v1/node/info

- 7 .  Generate a list of all applications currently running on node1.

- # curl -X GET http://node1:8042/ws/v1/node/apps

- Result

- You have now:

- Used CLI user and administrator commands and run several simple YARN API calls.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Running Sample YARN Applications

- About This Lab

- Objective:

To run YARN applications from the CLI and use the Ambari Pig and HiveViews

- File locations:

N/A

- Successful outcome:  You will: Use the command line to run a sample MapReduce job and

interactive Pig and Hive commands; install, configure, and use the AmbariPig View; and install, configure, and use the Ambari Hive View.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

YARN Applications

- Running YARN Applications from the CLI

- Run YARN applications from the command line.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Change to the /usr/hdp/2.3.0.0-2557/hadoop-mapreduce directory.

- # cd /usr/hdp/2.3.0.0-2557/hadoop-mapreduce

- 3 .  Run a sample program that uses MapReduce2 to calculate the value of pi.

- # yarn jar hadoop-mapreduce-examples.jar pi 5 10

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 4 .  The program returns an estimated value for pi.

- 5 .  Open the Firefox browser on the Ubuntu desktop and type the URL

node1:8088/cluster/apps/FINISHED to view information about this application.

- 6 .  Go back to the node1 terminal window and launch the Grunt shell, which allows you to run

interactive Pig commands.

- # pig

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 7 .  Run the mkdir command and create a directory named cmd_line_test in the current user’s

home HDFS directory.

- grunt > mkdir cmd_line_test;

Remain logged into the Grunt shell.

- 8 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 9 .  Log in as admin with a password of admin and browse to the HDFS Files View you created in a

previous lab.

- 10 . Browse to /user/root and confirm that the cmd_line_test directory was created.

Why are the New Directory and Upload buttons disabled?

- 11 . Return to the terminal window and exit the Grunt shell by issuing the quit command.

- grunt > quit;

- 12 . Hive queries can be executed from the CLI by using the Hive shell, which is accessed by

issuing the hive command.

- # hive

- 13 . Use the Hive shell to create a new database called hive_cmd_line.

- hive > create DATABASE cmd_line_hive;

NOTE

If you forget to put the semi-colon (;) at the end of the command, a newline prompt (>) isdisplayed. If this occurs, type a semi-colon (;) at the newline prompt and press Enter to finishthe command.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 14 . Verify that this operation was successful by typing the show DATABASES command.

- hive > show DATABASES;

- 15 . Remove this database using the drop command.

- hive > drop DATABASE cmd_line_hive;

- 16 . Use the quit command to exit the Hive shell.

- hive > quit;

- Using Ambari Pig View

- Install, configure, and use the Ambari Pig View.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 4 .  Click Configs and then click the Advanced tab.

Ensure that the HDFS Default configuration group is selected.

Scroll down to find and expand the Custom core-site section and change the values ofhadoop.proxyuser.hcat.groups and hadoop.proxyuser.hcat.hosts to *.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

NOTE

The values hadoop.proxyuser.root.groups=* and hadoop.proxyuser.root.hosts=*were added in another lab that configured the Ambari Files View.

If that lab has not been completed yet, these values need to be added here as well using theAdd Property link.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 5 .  Click Save to save the modifications.

Click Save again in the Save Configuration window.

Click OK in the confirmation window.

- 6 .  Restart any services as indicated in the Ambari Web UI.

- 7 .  In the Ambari Web UI, click Services and select Hive.

- 8 .  Click Configs and then click the Advanced tab.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 9 .  Scroll down to find and expand the Custom webhcat-site section and add the values

webhcat.proxyuser.root.groups=* and webhcat.proxyuser.root.hosts=*

via the Add Property link and click Add.

- 10 . Click Save to save the modifications.

Click Save again in the Save Configuration window.

Click OK in the confirmation window.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 11 . Restart any services as indicated in the Ambari Web UI.

- 12 . Select Manage Ambari from the admin menu button in order to initiate the process of

creating an instance of an Ambari View.

- 13 . Click Views.

- 14 . Click to expand Pig and then click Create Instance.

- 15 . In the Details section, enter:

Pig_01 as the Instance Name,  My Pig Interface as the Display Name,  and Pig viewfor the ETL team as the Description.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

Then scroll down and click Save.

- 16 . Scroll down and locate the Permissions section.

Beneath Grant permission to these users, click Add User, then click New and typeadmin.

Click the blue check box to save your change.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 17 . Click the Views icon and select the View named My Pig Interface.

- 18 . Click New Script to create a new Pig script in the admin user’s HDFS home directory.

Name the new script SimpleDemo and then click Create.

- 19 . For a proof of concept, create a script that employs the mkdir command to create a new

directory called pig_script_confirmation in the user’s HDFS home directory.

Do not forget to type the semi-colon at the end of the line below.

- mkdir pig_script_confirmation;

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 20 . Click Save and then click Execute to run the script.

The script will display a status of RUNNING for a few seconds, and then show as COMPLETED.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 21 . Select the HDFS Files View that you created in a previous lab.

- 22 . Browse to /user/admin and confirm that the pig_script_confirmation directory was

created.

- Using Ambari Hive View

- Install, configure, and use the Ambari Hive view.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  In the Ambari Web UI, click Services and select HDFS.

- 4 .  Click Configs and then click the Advanced tab.

Ensure that the HDFS Default configuration group is selected.

Scroll down to find and expand the Custom core-site section and confirm that the valueshadoop.proxyuser.root.groups=* and hadoop.proxyuser.root.hosts=* exist.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

These should have been added already when configuring the Ambari Files View in an earlierlab, and confirmed in the Ambari Pig View lab.

If those labs have not been completed yet, these values need to be added here as well at thispoint via the Add Property link.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 5 .  Select Manage Ambari from the admin menu button in order to initiate the process of

creating an instance of an Ambari View.

- 6 .  Click Views.

- 7 .  Click to expand Hive and then click Create Instance.

- 8 .  In the Details section, enter:

Hive_01 as the Instance Name,

My Hive Interface as the Display Name,

Hive view for the Data Analytics team as the Description.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

Then scroll down and click Save.

- 9 .  Scroll down and locate the Permissions section.

Beneath Grant permission to these users, click Add User, then click New and typeadmin.

Click the blue check box to save your change.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 10 . Click the Views icon and select the View named My Hive Interface.

- 11 . Create a query to create a database named hive_test, then click the Execute button. Do

not forget to type the semi-colon at the end of the line.

create DATABASE hive_test;

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Running Sample YARN Applications

- 12 . To the left of the Query Editor, note that the Database Explorer only shows a single database

named default. Click on the refresh symbol.

A database named hive_test should appear in the list of databases.

- Result

- You have now:

- Used the command line to run a sample MapReduce job and interactive Pig and Hive commands;

- installed, configured, and used the Ambari Pig View; and installed, configured, and used the Ambari

- Hive View.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

- Lab: Adding, Decommissioning, and Recommissioning

- Worker Nodes

- About This Lab

- Objective:

To use the Ambari Web UI to add two worker nodes, decommission andrecommission a worker node, change the HDFS replication factor tothree, and balance HDFS data blocks across DataNodes

- File locations:

N/A

- Successful outcome:

You will: Add two nodes to the cluster, decommission and thenrecommission one of the nodes, turn off maintenance mode, change thedefault replication factor to three, and run the HDFS balancer.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Adding, Deleting, and Replacing Worker Nodes

- Adding Worker Nodes

- Add two worker nodes to your cluster.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Click Hosts to open the Hosts page.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 4 .  Click the Actions menu button and select Add New Hosts.

- 5 .  Under Target Hosts, type the host names node2 and node3.

Because of the unique classroom lab environment a fully qualified domain name is notnecessary.

However, in most “real world” cluster installations, a fully qualified domain name is required forproper installation and cluster operation.

- 6 .  Scroll down in the window and under Host Registration Information click Browse.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 7 .  On the Ubuntu Desktop, select training-keypair.pem and click Open.

Once you see the private RSA key displayed, click Register and Confirm.

- 8 .  Because of the normal requirement of using fully qualified domain names,

you will get a Warning window about not using FQDNs. Click OK to dismiss the window andcontinue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 9 .  Monitor the agent installation progress window.

The agent is installed and registered and then a series of system checks are performed on thenodes to be installed.

You will receive a few warnings but these can be ignored in the lab environment.

Click Next to continue the installation.

- 10 . A Confirmation window opens and warns that some of the host checks failed.

The failures are minor in the lab environment and will not cause problems.

Click OK to dismiss the window and continue the installation.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 11 . The Assign Slaves and Clients window is where you choose which cluster nodes will run which

worker processes. Worker processes perform most of the data processing in a cluster.The more nodes that you have running worker processes, the more work that can be

simultaneously accomplished.

If necessary, click the DataNode, NodeManager, and Client check boxes for node2 andnode3.  Then click Next to continue.

- 12 . If these nodes should belong to any specific Ambari Configuration Group you can select it in

the Configurations window.

Both of the new nodes should belong to the default configuration group for each service, sojust click Next.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 13 . Review your selections for accuracy and then click Deploy.

- 14 . Monitor the installation progress.

- 15 . When the progress window indicates that the installation has completed, click Next.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 16 . Read the Summary window and click Complete.

- 17 . The lists of hosts should now include node1, node2, and node3.

- Decommissioning Worker Nodes

- Decommission a worker node.

- 1 .  If necessary, click Hosts in the Ambari Web UI.

- 2 .  Click node3 in the list of cluster nodes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 3 .  Click the Host Actions menu button and select Turn On Maintenance Mode.

- 4 .  In the Confirmation window, click OK.

- 5 .  Read the information in the Information window, and click OK.

- 6 .  Notice the new message above the Host Actions menu button.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 7 .  Find the DataNode listed in the node3 window.

Click the Started menu button and select Decommission.

- 8 .  In the Confirmation window, click OK.

- 9 .  Monitor the Background Operations Running window until the Decommission DataNode

process has completed.

Then click OK to dismiss the window.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 10 . The DataNode should be listed as Decommissioned.

- 11 . If you were going to take the node offline, you can also stop the DataNode process.

Click the Decommissioned menu button and select Stop.

- 12 . In the Confirmation window, click OK.

- 13 . Monitor the Background Operations Running window until the Stop DataNode process has

completed.

Then click OK to dismiss the window.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 14 . Find the NodeManager listed in the node3 window

Click the Started menu button and select Decommission.

- 15 . In the Confirmation window, click OK.

- 16 . Monitor the Background Operations Running window until the Decommission NodeManager

process has completed.

Then click OK to dismiss the window.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 17 . The DataNode should be listed as Decommissioned and stopped.

- 18 . Ambari updates the /etc/hadoop/conf/dfs.exclude and

/etc/hadoop/conf/yarn.exclude files by adding the host name of the decommissionedDataNode and NodeManager.

View the contents of these files now by opening a terminal window on the Ubuntu desktop andusing SSH to connect to node1.

- # ssh node1

- # more /etc/hadoop/conf/dfs.exclude

- # more /etc/hadoop/conf/yarn.exclude

- The node3 host name should be listed in each file.

- Recommissioning Worker Nodes

- Recommission a worker node.

- 1 .  On the node3 page in the Ambari Web UI, start the DataNode process by clicking the

Decommissioned menu button and selecting Start.

- 2 .  In the Confirmation window, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 3 .  Monitor the Background Operations Running window until the Start DataNode process has

completed.

Then click OK to dismiss the window.

- 4 .  For the DataNode, click the Decommissioned menu button and select Recommission.

- 5 .  In the Confirmation window, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 6 .  Monitor the Background Operations Running window until the Recommission DataNode

process has completed.

Then click OK to dismiss the window.

- 7 .  For the NodeManager, click the Decommissioned menu button and select Recommission.

- 8 .  In the Confirmation window, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 9 .  Monitor the Background Operations Running window until the Recommission DataNode and

Start NodeManager processes have completed.

Then click OK to dismiss the window.

- 10 . Ambari updates the /etc/hadoop/conf/dfs.exclude and

/etc/hadoop/conf/yarn.exclude files by removing the host name of the decommissionedDataNode and NodeManager.

View the contents of these files now by opening, if necessary, a terminal window on the Ubuntudesktop and then using SSH to connect to node1. (A terminal window might already be open tonode1.)

- # more /etc/hadoop/conf/dfs.exclude

- # more /etc/hadoop/conf/yarn.exclude

The node3 host name should not be listed in either file.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- Turning Off Maintentance Mode

- Turn off maintenance mode.

- 1 .

On the node3 page in the Ambari Web UI,

Click the Host Actions menu button and select Turn Off Maintenance Mode.

- 2 .  In the Confirmation window, click OK.

- 3 .  Read the information in the Information window and then click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- Changing the Replication Factor

- Change the default HDFS data block replication factor using the Ambari Web UI.

- Now that there are three DataNodes in the cluster, it makes sense for HDFS to automatically replicate

- each data block across all three DataNodes. This behavior makes HDFS more resilient to individual

- DataNode failures and can increase HDFS performance as well.

- 1 .  In the Ambari Web UI, click Services and then select HDFS.

- 2 .  Click the Configs page and then click Advanced.

Ensure that the HDFS Default configuration group is selected.

- 3 .  Scroll down to the General section and find the Block replication property.

Change it from 1 to 3.

(It was changed from the default installation value of 3 to 1 in a previous lab.)

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 4 .  Click Save to save the change to the HDFS configuration.

- 5 .  Type an optional description of the change that you made and then click Save again.

- 6 .  Click OK in the status window.

- 7 .  Restart any services that require restarting as indicated in the Ambari Web UI.

- Viewing DataNode and Replication Information

- View the number of DataNodes and replication information.

- 1 .  In a terminal window that is logged in to node1, assume HDFS superuser permissions.

- # su - hdfs

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 2 .  Run the HDFS fsck command on the HDFS / directory.

- $ hdfs fsck /

Use the command output to answer the following questions:

How many DataNodes are there?

There should be three.

What is the default replication factor for HDFS?

It should be three.

What is the average block replication?

It should be less than three.

Why is the average block replication less than three?

Because some files were created before the default replication factor was increased to three.What is the number of under-replicated blocks?

It should be zero.

- 3 .  Assume normal root user HDFS permissions again.

- $ exit

- 4 .  Use the HDFS Shell –ls command to view replication information for the /user/root/hosts

file.

- # hdfs dfs -ls

What is the replication factor for the hosts file?

This file was created in another lab and during the time period when the default replicationfactor

was one so the replication factor should be listed as one.

- 5 .  As the root user, run the HDFS fsck command on the /user/root/hosts file.

- # hdfs fsck /user/root/hosts

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

Use the command output to answer the following questions:

What is the total number of blocks in this file?

It should be one. This is a small file with a single data block.

What is the average block replication for the file?

It should be one, which means that the single data block is not replicated.

What is the number of under-replicated blocks?

It should be zero, which means that the single data block does not have to be replicated.What is the default replication factor?

It should be reported as three, although the file was created when the default replication factorwas one.

- 6 .  Use the HDFS Shell –setrep command to increase the replication factor of the

/user/root/passwd file to three.

- # hdfs dfs -setrep -w 3 /user/root/hosts

- 7 .  Run the HDFS Shell –ls command and the fsck command to view replication information

for the /user/root/hosts file.

- # hdfs dfs -ls

- # hdfs fsck /user/root/hosts

Use the command output to answer the following questions:

From the –ls command, has the replication factor been increased to three?

It should be three.

What is the total number of blocks in this file?

It should be one. This is a small file with a single data block.

What is the average block replication for the file?

It should be three. This means that there are three copies of the single data block in this file.What is the number of under-replicated blocks?

It should be zero.

- 8 .  Upload the local file /etc/networks to the HDFS /user/root directory.

- # hdfs dfs -put /etc/networks /user/root

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 9 .  Run the HDFS Shell –ls command and the fsck command to view replication information

for the /user/root/networks file.

- # hdfs dfs -ls

- # hdfs fsck /user/root/networks

Use the command output to answer the following questions:

From the –ls command, is the replication factor three?

It should be three.

What is the total number of blocks in this file?

It should be one. This is a small file with a single data block.

What is the average block replication for the file?

It should be three. This means that there are three copies of the single data block in this file.What is the number of under-replicated blocks?

It should be zero.

- 10 . Run the HDFS fsck command on the /user/root/networks file with

the –files –blocks –locations options.

- # hdfs fsck /user/root/group -files -blocks -locations

Do you see a data block number along with a location on each of the three DataNodes?You should.

- Rebalancing HDFS Storage

- Check and rebalance HDFS storage.

- Whenever you add more DataNodes, the new DataNodes are initially under-utilized because they do

- not contain any data blocks.  Running the HDFS balancer will move data blocks to the new DataNodes.

- 1 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 2 .  Click Quick Links and select NameNode UI.

- 3 .  Click the DataNodes tab in the NameNode UI.

- 4 .  For the three DataNodes, compare the numbers in the Used, Blocks, and Block pool used

columns.

The more evenly matched the numbers are across the DataNodes, the more balanced the datablocks are across the DataNodes.

NOTE

There is very little data in HDFS in the current lab environment so any differences betweenDataNodes will be very small. However, node2 and node3 were just added to the cluster, whichmeans that node1 might have slightly more data blocks.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

- 5 .  OPTIONAL

In a terminal window logged in to node1, become the HDFS superuser, and run the commandhdfs dfsadmin –report.

- # su - hdfs

- # hdfs dfsadmin -report

Compare the DFS Used and DFS Remaining values to determine HDFS balance.

- 6 .  In the Ambari Web UI, ensure that Services and HDFS are selected.

- 7 .  Click the Service Actions menu button and then select Rebalance HDFS.

- 8 .  In the Rebalance HDFS window, accept the default of ten percent and click Start.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Adding, Decommissioning, and Recommissioning Worker Nodes

If the DataNodes are balanced to within ten percent the balancer program will not take anyaction other than just evaluating the DataNodes. No data blocks will be moved.

If the DataNodes are not balanced to within ten percent then the balancer program

will shuffle data blocks between DataNodes.

- 9 .  Monitor the Background Operations Running window until the Rebalance HDFS process has

completed.

Then click OK to dismiss the window.

Because there is so little data, and the default replication factor was one when most of theHDFS files were created, the balancer might not shuffle any data blocks.

- Result

- You have now:

- Added two nodes to the cluster, decommissioned and recommissioned one of the nodes, turned off

- maintenance mode, changed the default replication factor to three, and run the HDFS balancer.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Setting Up for Capacity Scheduler Labs

- About This Lab

- Objective:

To create user home directories and Linux users and groups inpreparation for capacity scheduler labs

- File locations:

N/A

- Successful outcome:

You will: Create an HDFS home directory for each user identified inthe classroom scenario; configure a Linux group matching each homedirectory; and create Linux accounts for each home directory withmemberships in the appropriate groups.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

The YARN Capacity Scheduler

- Creating Home Directories

- Create an HDFS home directory for each user identified in the classroom scenario and

- assign that user ownership of the directory.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Switch to the hdfs user

- # su - hdfs

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Setting Up for Capacity Scheduler Labs

- 3 .  Run the commands necessary to create an HDFS home directory for each user listed below:

dev01, dev02, dev13

qa01, qa02, qa05

sales01, sales02, sales04

promo01, promo02

support01, support02, support09

Syntax:

$ hdfs dfs -mkdir /user/<user name>

$ hdfs dfs -chown <user name>:<user name> /user/<user name>

The commands for user dev01 are shown below. These commands should be repeated foreach user account created in this lab.

- $ hdfs dfs -mkdir /user/dev01

- $ hdfs dfs -chown dev01:dev01 /user/dev01

- 4 .  When you have created and changed ownership of all of the home directories, type exit to

return to normal root user permissions.

- $ exit

- Creating Linux Groups

- 1   Create Linux groups named promo, sales, dev, and qa using the groupadd command.

- # groupadd promo

- # groupadd sales

- # groupadd dev

- # groupadd qa

- Creating Linux User Accounts

- 1   Use the useradd command to create Linux accounts on node1 that have the same name as the

home directories you have created, with membership in the appropriate groups.

It is not necessary to set up a password for the users for lab purposes.

- # useradd <user name> -G <group name>

The example below demonstrates the command for user dev01:

- # useradd dev01 -G dev

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Setting Up for Capacity Scheduler Labs

Repeat until all users have been created and added to the groups as follows:

dev - dev01, dev02, dev13

promo - promo01, promo02

qa -  qa01, qa02, qa05

sales - sales01, sales02, sales04

- 2   Create the three supportXX users

NOTE

When you create the three supportXX users, you will not use  –G or provide a group namebecause they are not members of a group.

- # useradd support01

- # useradd support02

- # useradd support09

- Result

- You have now:

- Created an HDFS home directory for each user identified in the classroom scenario; configured a Linux

- group matching each home directory; and created Linux accounts for each home directory with

- memberships in the appropriate groups.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Managing YARN Containers and Queues

- About This Lab

- Objective:

To test the consequences of making changes to container sizes,

Maximum Application settings, and queue states; configure applicationpreemption and create a set of queues and leaf queues which logicallyrepresent the organizations you support and their SLAs

- File locations:

N/A

- Successful outcome:

You will: Prepare for the lab exercise, compare resource usage based oncontainer configuration, test queue settings and state behavior andconfigure queues to meet service level agreement (SLA) requirements.- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

The YARN Capacity Scheduler

- Lab Preparation

- Prepare for the lab exercise.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Change to the /usr/hdp/2.3.0.0-2557/hadoop-mapreduce directory.

- # cd /usr/hdp/2.3.0.0-2557/hadoop-mapreduce

- 3 .  Open a second terminal window and again use SSH to log in to node1.

- # ssh node1

- 4 .  Once again, change to the /usr/hdp/2.3.0.0-2557/hadoop-mapreduce directory.

- # cd /usr/hdp/2.3.0.0-2557/hadoop-mapreduce

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserve d.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 5 .  Position the two terminal windows so that both are visible on your screen side-by-side.

- 6 .  Type the MapReduce command to calculate pi in both terminal windows

but do not press Enter to execute it.

- # yarn jar hadoop-mapreduce-examples.jar pi 5 10

Type, but again do not execute, the same command in the second window.

- 7 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 8 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 9 .  Click Services in the Ambari Web UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 10 . Select the YARN service on the Services page.

- 11 . Click Quick Links and select ResourceManager UI.

The ResourceManager UI Web interface opens in another browser tab.

NOTE

Depending on your lab environment, the default URL to the ResourceManager UI could beblocked. This is an artifact of the lab environment, and not likely an issue you would experiencein the real world. If simply clicking the quick link fails to open the ResourceManager UI, replacethe default URL in the browser tab with node1:8088.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 12 . Click on the RUNNING link.

No applications are currently running.

This page will be refreshed in a moment once applications are running. Leave this tab open.- 13 . Go back to the Ambari Web UI YARN Services page and click Configs.

Note the default minimum container size.

- Comparing Resource Usage

- Compare resource usage based on container configuration.

- 1 .  Launch two instances of the YARN job that estimate pi by clicking on the first terminal window

and pressing the Enter key, then immediately clicking on the second terminal window andpressing the Enter key again.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 2 .  Quickly click the ResourceManager UI browser tab and refresh the RUNNING jobs page.

Continue refreshing until the page reports more than two containers have been provisioned.Note the maximum total number of containers and the total cluster memory that is able to beutilized by the applications.

NOTE

Your numbers may differ from the screen captures if the total resources available or defaultcontainer configuration varies.

- 3 .  Once the applications have finished running, click on the YARN Services Configs tab.

Using the scroll bar, adjust the Minimum Container Size (Memory) up to approximately60% of the default Maximum Container Size (Memory) setting.

NOTE

By default, the maximum container size will equal the total memory available to YARN pernode. In the example shown, the maximum container size is approximately 12 GB, so theminimum container size was set to approximately 7 GB.

Ask your instructor for the settings to use if your configuration differs from what is shown.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 4 .  Click Save to save the modifications.

Click Save again in the Save Configuration window.

Click OK in the Dependent Configurations window presented by the Ambari Guided

Configuration feature to accept all suggested changes.

Then click OK in the confirmation window.

- 5 .  Restart any services as indicated in the Ambari Web UI.

- 6 .  Return to your two terminal windows.

In each one, press the Up Arrow on your keyboard to display the previous yarn jar command.- 7 .  As before, press the Enter key in each terminal window and then quickly click the

ResourceManager UI browser tab, which should still be on the RUNNING information page.Once again, refresh the page until more than two containers are shown as provisioned.Note the maximum total number of containers and total amount of memory the applications areable to use this time.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

Why are the applications able to access less cluster memory with this set of jobs than they didbefore?

What is the maximum number of YARN jobs that could be provisioned and running at a time onthis cluster given the current configuration?

Remember that each job requires a container for the ApplicationMaster in addition to anyscheduled jobs.

- 8 .  To undo the YARN configuration changes, click on the Ambari Web UI YARN Services page

and click Configs.

Find the V1 configuration settings box and click on it.

- 9 .  Click the green Make V1 Current button, accept all dependent configuration suggestions,

and then restart any affected services.

If you want to confirm all settings are back to the default, run the two YARN applications onemore time in the terminal windows and confirm the number of containers provisioned andmemory used match the results from the first part of this lab section.

- Testing Queue Settings and Behavior

- Test queue settings and state behavior.

- 1 .  Click the Views icon and select the View named YARN Queue Manager.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

The YARN Queue Manager View opens.

- 2 .  Click the default queue to view its settings.

Under Scheduler, find the Maximum Applications setting and change it to 0.

The Actions menu button will turn orange.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

Click it, and select Save and Refresh Queues.

A Notes window opens asking you to describe what you have changed.

Make a note, and then click Save Changes.

It will take a few seconds for the queues to refresh.

At the top of the Ambari Web UI, you will see a blue notification box appear that lists 1 op asrunning.

When the queue refresh is complete, the box will turn gray and will display 0 ops.

- 3 .  Return to either open terminal window and press the Up Arrow key to display the previous yarn

jar command.

Then press the Enter key.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 4 .  The application should fail to launch.

Scroll up in the command output until you locate the java.io.IOException notification.This explains that the queue already has 0 applications, and therefore cannot accept any more.- 5 .  Return to the YARN Queue Manager and set Maximum Applications to 1. Then Save and

Refresh Queues as before.

- 6 .  Open both terminal windows and press the Up Arrow key so that they are both ready to run

the yarn jar command.

- 7 .  Press the Enter key with one of the terminal windows highlighted,

then quickly switch to the other terminal window and press the Enter key there as well.- 8 .  NOTE: There may be some lag when attempting to switch to the other terminal window,

however there should be sufficient time to launch the second application before the first onefinishes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

Note that the first job successfully launches and runs.

The second job, however, fails.

Scroll up in the command output and locate the java.io.IOException message.

Note that this time it identifies that the queue already has one application running, andcannot accept the submission of an additional application.

- 9 .  Go back to the YARN Queue Manager and set Maximum Applications back to 10000.

(10,000) Once again, click Save and Refresh Queues.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 10 . Once the queue refresh operation has completed, return to either one of the open terminal

windows, click the Up Arrow key to display the yarn jar command, and press the Enter key.- 11 . While this job is running, quickly go back to the YARN Queue Manager, and note the current

State of the queue is Running.

- 12 . Click the Stopped  button. Then quickly click Save and Refresh Queues.

(Note: You should be able to perform all of these tasks while the job you launched is stillrunning.)

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 13 . Note that stopping the queue while an application is running might in fact cause a temporary

halt...

…however the application will continue to run, and should successfully complete.

- 14 . After all applications have finished, with the default queue still stopped,

click the Up arrow in a terminal window and display the yarn jar command,

then press the Enter key to try to start a new application.

The application will fail with a YARN exception that states the queue is STOPPED and cannotaccept the application submission.

Leave the default queue in the STOPPED state.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- Configure queues to meet SLA requirements

- Configure queues to meet service level agreement (SLA) requirements according to the

- following scenario:

<table align="center">
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
</table>

- Preemption is enabled on the cluster so that minimum guarantees will be available to users.

- Configure two leaf queues for the Engineering queue with the following characteristics:

<table align="center">
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
	<tr align="center">
		<td></td>
		<td></td>
		<td></td>
	</tr>
</table>

- 1 .  Begin by removing all resources from the default queue by setting both the minimum and

maximum capacity settings to 0%.

- 2 .  Click the root queue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 3 .  With the root queue highlighted, click the Add Queue button above it.

- 4 .  The Enter queue path text box is displayed.

Type Engineering in the text box, then click the green checkmark button to the right.- 5 .  Note that the Engineering queue is created with all available resources assigned to it (currently

100%) by default.

Set the Capacity value to 60% and leave the Max Capacity value at 100%.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im5](images/Im5)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 6 .  Click the root queue.

- 7 .  With the root queue highlighted, once again click the Add Queue button above it.

- 8 .  The Enter queue path text box is displayed.

Type Marketing in the text box, then click the green checkmark button to the right.

- 9 .  Note that the Marketing queue is created with all available resources assigned to it (currently

40%) by default.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im5](images/Im5)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

Set the Capacity value to 30% and the Max Capacity value to 100%.

- 10 . Click the root queue.

- 11 . With the root queue highlighted, once again click the Add Queue button above it.

- 12 . The Enter queue path text box is displayed.

Type Support in the text box, then click the green checkmark button to the right.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im5](images/Im5)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 13 . Note that the Support queue is created with all available resources assigned to it (currently

10%) by default.

Leave the Capacity value at 10% and set the Max Capacity value to 100%.

- 14 . Next create the Engineering leaf queues.

Start by clicking the Engineering queue.

- 15 . Click the Add Queue button.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 16 . In the text box, type Dev and click the green checkmark button.

- 17 . Note that the Dev leaf queue is created with all available resources assigned to it (currently

100% of the resources available to the Engineering queue) by default.

Set the Capacity value to 50% and leave the Max Capacity value at 100%.

- 18 . Once again, click the Engineering queue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 19 . Click the Add Queue button and type QA in the text box. Then click the green checkmark

button.

- 20 . Note that the QA leaf queue is created with all available resources assigned to it (currently 50%

of the resources available to the Engineering queue) by default.

Leave the Capacity value at 50% and set the Max Capacity value to 100%.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 21 . Click the orange Actions menu button and select Save and Refresh Queues.

Type notes to describe what was changed, then click Save changes.

- 22 . To set preemption, in the Ambari Web UI click Services and select YARN.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 23 . Click the Configs tab.

- 24 . Under YARN Features, set the Pre-emption setting to Enabled.

- 25 . Click the green Save button.

Add notes to indicate what was changed.

Click Save.

Then click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN Containers and Queues

- 26 . Restart any services as indicated in the Ambari Web UI.

- Result

- You have now:

- Perpared for the lab exercise, compared resource usage based on container configuration, tested

- queue settings and state behavior, and configured queues to meet service level agreement (SLA)

- requirements.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Managing YARN ACLs and User Limits

- About This Lab

- Objective:

To configure queue settings so that minimum user limit settings arestrictly enforced

- File locations:

N/A

- Successful outcome:

You will: Configure YARN ACLs and default queue mapping; testminimum user limits; and re-establish access to the default queue.- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

The YARN Capacity Scheduler

- Lab Preparation

- Open multiple windows and log in as different user accounts in order to test YARN

- ACLs and user limits.

- 1 .  Open a terminal window on the Ubuntu desktop

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Switch to the dev01 user.

- # su - dev01

- 3 .  When you switch to this user, the prompt should look like this:

- 4 .  Open another terminal window.

Use SSH to log in to node1

Switch to the qa01 user in this window.

- # ssh node1

- # su - qa01

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

Repeat this process for all of the following users, each one in a new terminal window.

When you are finished, you should have five open terminals, each one acting as a differentuser.

promo01

support01

sales01

Position the terminal windows so that you can move between them easily.

NOTE

Make sure that the prompt in each window lists <user name>@node1 not <user

name>@ubuntu. If Ubuntu is listed (or if you received an error regarding no HOME directory),you have missed the step to use SSH to connect to node1 prior to creating the user, and thenext step in the lab will fail.

- 5 .  In each open terminal, change directories to /usr/hdp/2.3.0.0-2557 /hadoop-

mapreduce.

- $ cd /usr/hdp/2.3.0.0-2557/hadoop-mapreduce

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- Configuring YARN ACLs and Default Queue Mapping

- Configure YARN ACLs and default queue mapping.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Click the Views icon and select the View named YARN Queue Manager.

The YARN Queue Manager View opens.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- 3 .  Because queue permissions are cumulative from the top level down, you want to start by

removing all permissions from default root queue for everyone except the admin user.To do this, click on the root queue and locate the Submit Applications setting.

Click the Custom button, and in the Users field that appears, type the word admin.

Leave the Groups setting blank.

- 4 .  Click the Dev queue under Engineering queue.

Under Access Control and Status, find the Submit Applications setting and click theCustom button.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- 5 .  Give members of the dev group access to this by typing dev in the Groups section.

- 6 .  Click the QA queue under Engineering queue.

Under Access Control and Status, find the Submit Applications setting and click theCustom button.

- 7 .  Give members of the qa group access to this by typing qa in the Groups section.

- 8 .  Next click the Marketing queue.

Again, under Access Control and Status find Submit Applications and click on the Custombutton. This time, add the sales and promo group to the list of allowed groups via a comma-separated list (no spaces).

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- 9 .  Click the Support queue, and again find the Submit Applications setting.

Click the Custom button, but this time in the section type a comma-separated list of the threeSupport users we provisioned in a previous lab: support01,support02,support09.- 10 . Now that ACLs have been set up to control queue access once the queues have been

refreshed, locate the Queue Mappings setting under Scheduler.

- 11 . Type the following comma-delimited list (no spaces or returns) into the Queue Mappings

settings box:

- u:support01:Support,u:support02:Support,u:support09:Support,

- g:promo:Marketing,g:sales:Marketing,g:dev:Dev,g:qa:QA

The syntax for queue mapping is:

User mappings format - u:<username>:<queuename>

Group mappings format - g:<groupname>:<queuename>

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- 12 . Click the orange Actions button and select Save and Refresh Queues.

Click the Save Changes button in the resulting pop-up.

- 13 . Now to test your settings and see if they worked, go to one of your open terminal windows and

type the yarn jar command you have been using in these labs for tests.

- # yarn jar hadoop-mapreduce-examples.jar pi 5 10

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

Repeat this process for at least a couple of users, then open a browser tab to

http://node1:8088.

You should see in the list of applications that various jobs are being or have been performed bydifferent users,

and that those jobs have been assigned to the appropriate queues.

- 14 . OPTIONAL:

If time allows, go back and change the ACL settings for the Dev queue and remove the devgroup from the Submit Applications list of allowed users.

Save and refresh the queues, then go to the terminal window where dev01 is logged in and tryto run the yarn jar job again.

What do you think will happen?

- Testing User Limits

- Test minimum user limits.

- 1 .  Open two terminal windows and use SSH to connect to node1. In the first one switch users to

qa01. In the second one switch users to qa02. Then in both terminal windows, change to the/usr/hdp/2.3.0.0-2557/hadoop-mapreduce directory as before, and type but do notexecute the test application yarn jar command.

First terminal window:

- # ssh node1

- # su - qa01

- $ cd /usr/hdp/2.3.0.0-XXXX/hadoop-mapreduce

- $ yarn jar hadoop-mapreduce-examples.jar pi 5 10

(Do not run the yarn jar command yet.)

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

Second terminal window:

- # ssh node1

- # su - qa02

- $ cd /usr/hdp/2.3.0.0-XXXX/hadoop-mapreduce

- $ yarn jar hadoop-mapreduce-examples.jar pi 5 10

(Do not run the yarn jar command yet.)

- 2 .  Execute the yarn jar command for qa01 and then immediately execute the yarn jar command

for qa02.

You should observe that both jobs execute at the same time. Then open a browser and point itto the ResourceManager UI at http://node1:8088 and confirm that both jobs ended withinjust a few seconds of each other.

- 3 .  Go back to the YARN Queue Manager View in the Ambari UI and click the Engineering.QA

queue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

Note that the default Minimum User Limit setting is 100%.

A minimum user limit of 100% should guarantee a single user 100% of the queue Capacitysetting.

Why were two users able to run jobs in this queue at the same time?

- 4 .  Disable elasticity settings for the queue.

To do this, change the Max Capacity value from 100% so that it matches the Capacity valueof 50%.

- 5 .  Click the Actions button and save and refresh the queues, make notes, and save changes.

Once the operation completes, go back to the two terminal windows, press the Up Arrow ineach to find the previous yarn jar command, and once again run the jobs one right after theother.

Did the jobs still run at basically the same time?

Can you figure out why this might have happened?

- 6 .  For minimum user limits to be strictly enforced, no elasticity can exist in queue settings.

This includes any parent queues.

Because the Engineering parent queue had elasticity enabled, the second job was allowed torun in that available capacity.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

Disable elasticity settings for the Engineering queue. To do this, in the YARN Queue Managerselect the Engineering queue and change the Max Capacity value from 100% to match theCapacity value of 60%.

- 7 .  Click the Actions button and save and refresh the queues, make notes, and save changes.

Once the operation completes, go back to the two terminal windows, press the Up Arrow ineach to find the previous yarn jar command, and once again run the jobs one right after theother.

This time, one job will wait for the other job to complete before it starts running.

The terminal window should report the second job taking approximately twice as long as thefirst one, and the ResourceManager UI should show the two jobs finishing farther apart than inour previous runs.

- Re-establishing Default Queue Access

- Re-establish access to the default queue.

- 1 .  Some actions (setting up high availability for the ResourceManager for example)  require the

ability to run a YARN job in the default queue as part of their self-test. These will report ashaving failed if this job cannot run properly.

To enable this, return to the YARN Queue Manager and set the capacity of the Engineeringqueue to 59%.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- 2 .  Then set the default queue Capacity setting to 1% and the Max Capacity to 100%.

NOTE

In the lab, make sure the Max Capacity setting allows for use of all cluster resources. Thedefault will be for the Max Capacity value to match the Capacity value, which in this casewould not be enough resources to allow an application to run.

- 3 .  With the default queue still selected, change the State to Running and make sure that Submit

Applications is set to Anyone.

- 4 .  Click the orange Actions button and select Save and Refresh Queues.

Click the Save Changes button in the resulting pop-up.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing YARN ACLs and User Limits

- Result

- You have now:

- Configured YARN ACLs and default queue mapping; tested minimum user limits; and reestablished

- access to the default queue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Configuring Rack Awareness

- About This Lab

- Objective:

To use the Ambari Web UI to configure rack awareness

- File locations:

N/A

- Successful outcome:

You will: View default rack awareness information; replace /default-rack with /rack01 on node1, /rack02 on node2, and /rack03 onnode3; and view the results of the new configuration.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Configuring Rack Awareness

- Viewing Rack Awareness Information

- View the default rack awareness configuration information.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  List the rack awareness files in the /etc/hadoop/conf directory.

- # ls /etc/hadoop/conf

Do you see the topology_mappings.data and topology_script.py files?

You should.

- 3 .  View the contents of the /etc/hadoop/conf/topology_mappings.data file.

- # cat /etc/hadoop/conf/topology_mappings.data

What is the rack name assigned to all three DataNodes?

It should be /default-rack.

- 4 .  Assume HDFS superuser permissions.

- # su - hdfs

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Configuring Rack Awareness

- 5 .  Run the HDFS fsck command with the –racks option.

- $ hdfs fsck -racks

What is the number of racks that is reported?

It should be one.

- 6 .  Run the HDFS dfsadmin command with the –report option.

- $ hdfs dfsadmin -report

You should see a Name: reported for each DataNode.

Do you see a Rack: name reported for any DataNode?

You should not.

- 7 .  Remain logged in with HDFS superuser permissions.

- Configuring Rack Awareness

- Configure rack awareness using the Ambari Web UI.

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Click Hosts in the Ambari Web UI.

- 4 .  Click node1 in the list of nodes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring Rack Awareness

- 5 .  With node1 selected, click the Host Actions menu button and select Set Rack.

- 6 .  Configure node1’s rack name as /rack01, and click OK.

- 7 .  Click Back to return to the list of cluster nodes.

- 8 .  Click node2 in the list of nodes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Configuring Rack Awareness

- 9 .  With node2 selected, click the Host Actions menu button and select Set Rack.

- 10 . Configure node2’s rack name as /rack02, and click OK.

- 11 . Click Back to return to the list of cluster nodes.

- 12 . Click node3 in the list of nodes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Configuring Rack Awareness

- 13 . With node3 selected, click the Host Actions menu button and select Set Rack.

- 14 . Configure node3’s rack name as /rack03, and click OK.

- 15 . Click Services and restart any service that requires restarting as indicated in the Ambari Web

UI.

HDFS and MapReduce2 should be indicated.

- Viewing Results of the Configuration

- View the results of configuring rack awareness.

- 1 .  Go back to the terminal window logged in to node1.

View the contents of the /etc/hadoop/conf/topology_mappings.data file.

- $ cat /etc/hadoop/conf/topology_mappings.data

What are the rack names of node1, node2, and node3?

They should be /rack01, /rack02, and /rack03.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring Rack Awareness

- 2 .  You should still have HDFS superuser permissions in the terminal window.

Run the HDFS fsck command with the –racks option again.

- $ hdfs fsck -racks

What is the number of racks that is reported?

It should be three.

- 3 .  Run the dfsadmin command again with the –report option.

- $ hdfs dfsadmin -report

Is the rack name for each DataNode reported?

It should be.

- 4 .  Assume normal root user permissions again.

- $ exit

- Result

- You have now:

- Viewed default rack awareness information; replaced /default-rack with /rack01 on node1,

- /rack02 on node2, and /rack03 on node3; and viewed the results of the new configuration.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Configuring NameNode HA

- About This Lab

- Objective:

To use the Ambari Web UI to configure a cluster with HDFS NameNode HA- File locations:

N/A

- Successful outcome:  You will: Configure an Active and a Standby NameNode running in your

cluster, three ZooKeeper Servers to support NameNode HA, a ZooKeeperFailoverController on each NameNode system, and three running

JournalNodes. You will also remove the existing Secondary NameNode andtest automatic failover.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Configuring HDFS and YARN High Availability (HA)

- Viewing Configurations

- View the NameNode and cluster configuration prior to configuring NameNode HA.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Search the /etc/hadoop/conf/core-site.xml file for the fs.defaultFS property.

Notice the value listed in this property.

- # more /etc/hadoop/conf/core-site.xml

The value of fs.defaultFS should be hdfs://node1:8020.

- 3 .  View the contents of the /etc/hadoop/conf/hdfs-site.xml file.

- # more /etc/hadoop/conf/hdfs-site.xml

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Do any of the following properties exist in the file?

dfs.client.failover.proxy.provider.mycluster

dfs.ha.namenode.mycluster

dfs.namenode.http-address.mycluster.nn1

dfs.namenode.http-address.mycluster.nn2

dfs.namenode.rpc-address.mycluster.nn1

dfs.namenode.rpc-address.mycluster.nn2

dfs.nameservices

None of these properties should exist.

(This is not a complete list of NameNode HA properties.)

- 4 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 5 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 6 .  Click Services and select HDFS.

On the Summary page do you see a NameNode and a Secondary NameNode

(SNameNode)?

You should see both.

Do you see any ZooKeeper FailoverControllers or JournalNodes?

You should not.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- Configuring ZooKeeper

- Configure ZooKeeper to support NameNode HA.

- 1 .  In the Ambari Web UI, click Services and select ZooKeeper.

How many ZooKeeper Servers are shown on the Summary page?

There should be only one.

You will need a minimum of three ZooKeeper Servers to support NameNode HA.

- 2 .  Click the Service Actions menu button and select Add ZooKeeper Server.

- 3 .  In the Confirmation window, ensure that node2 is selected.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Then click Confirm Add.

- 4 .  Monitor the Background Operations Running window for the progress of the Install ZooKeeper

Server process.

Click OK when the ZooKeeper Server is installed.

- 5 .  On the ZooKeeper service Summary page, is the new ZooKeeper Server running or not?

It should be visible but stopped.

You will start it later in this lab exercise.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 6 .  Click the Service Actions menu button again and select Add ZooKeeper Server.

- 7 .  In the Confirmation window, ensure that node3 is selected and click Confirm Add.

- 8 .  On the ZooKeeper service Summary page, has the new ZooKeeper Server started?

It should not be running.

- 9 .  Click the Service Actions menu button and select Start.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 10 . In the Confirmation window, click Confirm Start.

- 11 . Monitor the Background Operations Running window for the progress of the Start ZooKeeper

Server process.

Click OK when the ZooKeeper Servers have started.

- 12 . On the ZooKeeper service Summary page, have all three ZooKeeper Servers started now?

They should have.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 13 . Restart any other services that require restarting as indicated in the Ambari Web UI.

For example, YARN and Hive should be restarted.

- Enabling NameNode HA.

- Enable NameNode HA.

- 1 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 2 .  Click the Service Actions menu button and select Enable NameNode HA.

The Enable NameNode HA Wizard window opens.

- 3 .  Type mycluster as the Nameservice ID and then click Next.

(There is no HBase running on the cluster so ignore the message in the wizard.)

- 4 .  Ensure that the Active NameNode (Current NameNode) is on node1, the Standby

NameNode (Additional NameNode) is on node2, and that a JournalNode configured oneach of the three cluster nodes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Then click Next.

- 5 .  Read the information in the Review window.

Notice that automatic failover is enabled by default.

No changes are necessary so click Next (not shown) to continue.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 6 .  The wizard lists manual configuration steps that are required next.

These must be completed or the Next button in the wizard will not become active.

In the terminal window logged in to node1, which is the currently active NameNode system,type the commands shown in the wizard.

- # sudo su hdfs -l -c ‘hdfs dfsadmin -safemode enter’

The command output should report that safemode is ON.

- # sudo su hdfs -l -c ‘hdfs dfsadmin -saveNamespace’

The command output should report that save namespace is successful.

The Next button should become active in the wizard, so click Next.

- 7 .  In the Configure Components window, monitor the progress of the configuration.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Click Next when every item on the list has completed.

- 8 .  The wizard lists another manual configuration step that is required next.

This command must be completed or the Next button in the wizard will not become active.In the terminal window logged in to node1, which is the currently active NameNode system,type the command shown in the wizard.

- # sudo su hdfs -l -c ‘hdfs namenode -initializeSharedEdits’

You should see a large amount of screen output.

The last message should be a SHUTDOWN_MSG.

The Next button should become active in the wizard, so click Next.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 9 .  In the Start Components window, monitor the progress.

When the components have successfully started, click Next.

- 10 . The wizard lists more manual configuration steps that are required next.

The first command must be completed on the currently active NameNode system, which isnode1. The second command must be completed on the NameNode system that is beingadded, which is node2.

IMPORTANT NOTE

These commands must be completed, but there is a bug that prematurely enables the Nextbutton in the wizard. Do NOT click Next until after manually entering both commands!In the terminal window logged in to node1, which is the currently active NameNode system,type the command shown in the wizard.

- # sudo su hdfs -l -c ‘hdfs zkfc -formatZK’

You should see a large amount of screen output.

In the terminal window logged in to node1, use SSH to log in to node2.

Then run the second command listed in the wizard.

- # ssh node2

- # sudo su hdfs -l -c ‘hdfs namenode -bootstrapStandby’

You should see a large amount of screen output.

The last message should be a SHUTDOWN_MSG.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Log out of node2 by typing exit.

- # exit

Then click Next.

- 11 . In the Confirmation window click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 12 . Monitor the progress in the Finalize HA Setup window.

When the components have successfully started, click Done.

(This step might take several minutes to complete.)

- Verifying HA Configuration.

- Verify the new NameNode HA configuration

- 1 .  In the Ambari Web UI, click Services and select HDFS.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

On the Summary page:

How many NameNodes are there?

There should be two.

What types of NameNodes are there?

There should be an Active and Standby NameNode.

Is there a ZKFailoverController?

There should be.

Are there any JournalNodes running?

There should be three.

Click the HDFS Quick Links menu.

Do Quick Links exist to both NameNodes now?

There should be links to both.

- 2 .  In the terminal window logged in to node1, view the fs.defaultFS property in the

/etc/hadoop/conf/core-site.xml file.

- # more /etc/hadoop/conf/core-site.xml

What is the value of the property?

It should now be hdfs://mycluster.

- 3 .  View the contents of the /etc/hadoop/conf/hdfs-site.xml file.

- # more /etc/hadoop/conf/hdfs-site.xml

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

Do any of the following properties exist in the file?

dfs.client.failover.proxy.provider.mycluster

dfs.ha.namenode.mycluster

dfs.namenode.http-address.mycluster.nn1

dfs.namenode.http-address.mycluster.nn2

dfs.namenode.rpc-address.mycluster.nn1

dfs.namenode.rpc-address.mycluster.nn2

dfs.nameservices

All of these properties should exist now.

- Testing Failover

- Test Failover to the Standby NameNode.

- 1 .  In the Ambari Web UI on the Services > HDFS > Summary page. Then click the Active

NameNode link.

- 2 .  Find the Active NameNode in the list of components. Then click the Started menu button and

select Stop.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 3 .  In the Confirmation window, click OK.

- 4 .  In the Background Operations Running window, monitor the Stop NameNode process.

When it has finished, click OK.

The Active NameNode should be listed as Stopped.

- 5 .  Go back to the Services > HDFS > Summary page and either wait a minute or two or

manually refresh the browser.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring NameNode HA

The Summary panel should update and show the former Standby NameNode promoted to thenew Active NameNode and former Active NameNode as just a NameNode and stopped.- 6 .  Click the stopped NameNode in the list of components.

- 7 .  Find the NameNode in the list of components, click the Stopped menu button, and then select

Start.

- 8 .  In the Confirmation window, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Configuring NameNode HA

- 9 .  In the Background Operations Running window, monitor the Start NameNode process.

When it has finished, click OK.

- 10 . Use the information on the Services > HDFS > Summary page to ensure that there is an

Active and a Standby NameNode.

To see the change either wait for a browser update or manually refresh your browser.

- Result

- You have now:

- Configured an Active and a Standby NameNode running in your cluster, three ZooKeeper Servers to

- support NameNode HA, a ZooKeeper FailoverController on each NameNode system, and three running

- JournalNodes. You have also removed the existing Secondary NameNode and tested automatic

- failover.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Configuring ResourceManager HA

- About This Lab

- Objective:

To use the Ambari Web UI to configure a cluster with YARN

ResourceManager HA in order to have an Active and a StandbyResourceManager running in your cluster

- File locations:

N/A

- Successful outcome:

You will: View ResourceManager cluster configuration, verify there arethree ZooKeeper servers supporting ResourceManager HA, enableResourceManager HA using the Ambari Web UI, verify the new

ResourceManager HA configuration and failover to a Standby

ResourceManager.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Configuring HDFS and YARN High Availability

- Viewing ResourceManager Configuration Information

- View the ResourceManager and cluster configuration prior to configuring

- ResourceManager HA.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  View the contents of the /etc/hadoop/conf/yarn-site.xml file and find the property

yarn.resourcemanager.ha.enabled.

- # more /etc/hadoop/conf/yarn-site.xml

What is the value of this property?

It should be false.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 3 .  While still looking at the yarn-site.xml file, do any of the following properties exist?

yarn.client.failover-proxy-provider

yarn.resourcemanager.cluster-id

yarn.resourcemanager.ha.rm-ids

yarn.resourcemanager.hostname.rm1

yarn.resourcemanager.hostname.rm2

yarn.resourcemanager.webapp.address.rm1

yarn.resourcemanager.webapp.address.rm2

None of these properties should exist.

(This is not a complete list of ResourceManager HA properties.)

- 4 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 5 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 6 .  Click Services and select YARN.

On the Summary page do you see a ResourceManager and an App Timeline Server?You should see both.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- Verifying the Number of ZooKeeper Servers

- Verify there are three ZooKeeper Servers configured to support ResourceManager HA.

- 1 .  In the Ambari Web UI, click Services and select ZooKeeper.

How many ZooKeeper Servers are shown on the Summary page?

There should be three.

- Enabling ResourceManager HA

- Enable ResourceManager HA using the Ambari Web UI.

- 1 .  In the Ambari Web UI, click Services and select YARN.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 2 .  Click the Service Actions menu button and select Enable ResourceManager HA.

The Enable ResourceManager HA Wizard window opens.

- 3 .  Read the information in the Get Started panel and then click Next.

- 4 .  Ensure that the Active ResourceManager (Current ResourceManager) is on node1, and the

Standby ResourceManager (Additional ResourceManager) is on node2. Then click Next.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 5 .  Read the information in the Review window.

Notice that automatic recovery is enabled by default.

No changes are necessary so click Next (not shown) to continue.

- 6 .  In the Configure Components window, monitor the progress of the configuration.

Click Complete when every item on the list has completed.

(This step will take several minutes to complete.)

If there is any failure to start a service, a Retry button is presented in the wizard. Click it tocontinue starting components if necessary.

NOTE

If this fails more than once or twice, it is likely the default queue has not been configured toallow applications to run, or does not have sufficient resources available. You can view thedetailed error messages to confirm (look for the Pig Smoke Test job as the failure point.)If this happens, simply cancel the wizard. You will see an error message stating that you mustmanually roll back the configuration changes. However, the failed smoke test was the finalstep. You will find if you simply restart your cluster services that ResourceManager HAconfiguration has actually succeeded.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- Verifying  ResourceManager HA configuration

- Verify the new ResourceManager HA configuration.

- 1 .  In the Ambari Web UI, click Services and select YARN.

On the Summary page:

How many ResourceManagers are there?

There should be an Active and Standby ResourceManager.

Which cluster node is running the Active ResourceManager?

It is typically node2 at this point in the lab exercise.

- 2 .  Open a new tab in the Firefox browser running on the Ubuntu desktop.

In the browser tab type the URL http://node1:8088.

(This step assumes that the Active ResourceManager is running on node2.)

This should open the ResourceManager UI.

Did the ResourceManager UI open?

It should have.

- 3 .  Examine the ResourceManager UI URL again.

Is it still node1:8088 or was it redirected to node2:8088?

It should have been redirected to node2.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

Why?

It was redirected because any Web UI or YARN REST API request received by the

Standby ResourceManager is automatically redirected to the Active ResourceManagerby ResourceManager HA.

- 4 .  In the terminal window logged in to node1, view the contents of the

/etc/hadoop/conf/yarn-site.xml file.

- # more /etc/hadoop/conf/yarn-site.xml

- What is the value of the yarn.resourcemanager.ha.enabled property?

- It should be true.

- Do any of the following properties exist in the file?

- yarn.client.failover-proxy-provider

- yarn.resourcemanager.cluster-id

- yarn.resourcemanager.ha.rm-ids

- yarn.resourcemanager.hostname.rm1

- yarn.resourcemanager.hostname.rm2

- yarn.resourcemanager.webapp.address.rm1

- yarn.resourcemanager.webapp.address.rm2

- All of these properties should now exist.

- Testing Failover

- Failover to the Standby ResourceManager.

- 1 .  In the Ambari Web UI click on the Services > YARN > Summary page,

Click the Active ResourceManager link.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 2 .  Find the Active ResourceManager in the list of components,

Click the Started menu button, and then select Stop.

- 3 .  In the Confirmation window, click OK.

- 4 .  In the Background Operations Running window, monitor the Stop ResourceManager process.

When it has finished, click OK.

The Active ResourceManager should be listed as Stopped.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 5 .  Go back to the Services > YARN > Summary page and either wait a minute or two or

manually refresh the browser. The Summary panel should update and show the former StandbyResourceManager promoted to the new Active ResourceManager and former Active

ResourceManager as just a stopped ResourceManager.

- 6 .  Click the stopped ResourceManager in the list of components.

- 7 .  Find the ResourceManager in the list of components, click the Stopped menu button, and

then select Start.

- 8 .  In the Confirmation window, click OK.

- 9 .  In the Background Operations Running window, monitor the Start ResourceManager process.

When it has finished, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Configuring ResourceManager HA

- 10 . Use the information on the Services > YARN > Summary page to ensure that there is both

an Active and a Standby ResourceManager.

You might have to either wait for a browser update or manually refresh your browser.

- Result

- You have now:

- Viewed ResourceManager cluster configuration, verified there are three ZooKeeper servers supporting

- ResourceManager HA, enabled ResourceManager HA using the Ambari Web UI, verified the new

- ResourceManager HA configuration and performed a failover to a Standby ResourceManager.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Managing Ambari Alerts

- About This Lab

- Objective:

To use the Ambari Web UI to manage Ambari alerts

- File locations:

N/A

- Successful outcome:

You will: List alert definitions; disable, enable, and edit an alertdefinition; list alert instances and trigger an alert; and create a new alertgroup and notification.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Monitoring a Cluster

- Listing Alert Definitions

- List Ambari alert definitions in the Ambari Web UI.

- 1 .

Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URLhttp://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Click Alerts in the Ambari Web UI.

- 4 .  View the list of alert definitions on the Alerts page.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

How many alert definitions are there?

The number should be shown in the lower right-hand corner of the Alerts page.

- 5 .  Use the forward and back arrows beneath the alert definitions to view the entire list of alert

definitions.

- 6 .  Filter the list of displayed alert definitions by clicking the Groups menu button and selecting

YARN Default (8).

Only the eight YARN-related alert definitions are displayed.

- 7 .  Click the Groups menu button again and select All (45).

All 45 alert definitions are listed again.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 8 .  Select CRITICAL from the Status drop-down menu.

Only alerts with a CRITICAL status are displayed. There might not be any alerts with this status.- 9 .  Click the X icon next to the Status drop-down menu in order to clear the status filter.

All alert definitions are displayed again.

- 10 . Type ui in the Alert Definition Name text box to filter the list to only those alert definitions

that contain ui.

The alert definition list should contain only definitions with UI or ui in their name.

Do not remove ui from the Alert Definition Name filter text box.

- Working With Alert Definitions

- View, disable, enable, and edit an alert definition in the Ambari Web UI.

- 1 .  Click the NodeManager Web UI alert definition.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 2 .  View the alert definition in the Configuration panel.

Notice the Check Interval.

Notice the Thresholds response messages.

You will see examples of the response messages in other lab steps.

Response messages are editable.

- 3 .  If necessary, scroll down in the browser window to view the alert instances that were created

based on the alert definition.

Notice an example of a response message in the response column.

This is the response message for the OK status.

- 4 .  If necessary, scroll up in the browser window and click Enabled.

The Enabled link functions as a toggle and will disable the alert definition.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 5 .  In the Confirmation window, click Confirm Disable.

- 6 .  Wait for a minute and then refresh the browser window.

Then scroll down, if necessary, and view the alert instances again.

Are there any instances?

All instances should have been deleted.

- 7 .  Click Disabled to re-enable the alert definition.

- 8 .  In the Confirmation window, click Confirm Enable.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 9 .  Wait a minute or two and then refresh the browser window.

Then scroll down, if necessary, and view the alert instances again.

Are there any instances?

There should be three instances.

- 10 . Click Edit to change the NodeManager Web UI alert definition.

- 11 . Change the CRITICAL response message to Network or HTTP connection failed to

{1} ({3}).

Then click Save.

- Triggering an Alert

- Trigger and view an alert for the NodeManager Web UI.

- 1 .  In the Ambari Web UI, click Hosts to open the Hosts page.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 2 .  Click node3 in the list of cluster nodes.

- 3 .  On the Summary tab, find the NodeManager in the list of components.

Click the Started menu button and select Stop.

Stopping the NodeManager on node3 should trigger the NodeManager Web UI alert,

as well as other alerts.

- 4 .  In the Confirmation window, click OK.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 5 .  In the Background Operations Running window, monitor the Stop NodeManager process.

When it has finished, click OK.

- 6 .  Within a minute you should see alerts triggered.

Click on the red alerts notification at the top of the Ambari Web UI.

The Critical or Warning Alerts window opens showing all the current alerts.

- 7 .  Notice that the NodeManager Web UI alert has been triggered.

Also notice the custom response message.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 8 .  Click the NodeManager Web UI link to open the alert definition and alert instance list.

- 9 .  The alert instance that triggered is shown in the list of instances.

In the screen capture, the alert had been triggered for 17 minutes.

The alert had also been triggered 12 times in the last 24 hours.

(This was a result of lab development.)

The custom response message is also displayed.

- 10 . Click Edit to change the NodeManager Web UI alert definition.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 11 . Change the CRITICAL response message back to Connection failed to {1} ({3}).

Then click Save.

- 12 . Wait a minute and then look at the response message in the triggered alert.

Did it change?

It should have. It changed because the alert is re-checked every minute.

While the response message is updated, any configured email or SNMP notifications are notresent every minute. Notifications are only sent when the status changes.

- 13 . Click node3 (not YARN) in the list of alert instances.

- 14 . Click the Summary tab.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 15 . Find the NodeManager in the list of components.

Click the Stopped menu button and select Start.

Starting the NodeManager on node3 should remove the NodeManager Web UI alert, as well asother alerts.

- 16 . In the Confirmation window, click OK.

- 17 . In the Background Operations Running window, monitor the Start NodeManager process.

When it has finished, click OK.

Wait one minute, refresh the browser, and the alerts should be gone.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- Creating Alert Groups and Notifications

- Create an alert group and a notification.

- 1 .  In the Ambari Web UI, click Alerts.

- 2 .  Click the Actions menu button and select Manage Alert Groups.

This initiates the process of creating a new alert group.

The Manage Alert Groups window opens.

- 3 .  Click the plus (+) button beneath the list of alert groups.

The Create Alert Group window opens.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 4 .  In the Create Alert Group window, type the name HDFS Storage Alerts.

Click OK.

The new alert group appears in the list of alert groups in the Manage Alert Groups window.- 5 .  Ensure that the HDFS Storage Alerts group is selected, and then click the plus (+) button on

the right side of the window.

The Select Alert Group Definitions window opens.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 6 .  In the Select Alert Group Definitions window, click the Service menu button and select HDFS.

The list of Alert Definitions is filtered to only those that relate to HDFS.

The items on the Service and Component menu buttons can be selected and deselected.Clicking an item, like HDFS, selects the item.

Clicking the item again deselects the item.

Leave HDFS selected.

- 7 .  From the list of HDFS alert definitions, select Percent DataNodes With Available Space,

Percent DataNodes Available, HDFS Capacity Utilization, and DataNode Storage.NOTE

By default, only the first 10 alert definitions are visible, so you will need to go to the next pageto see all available settings.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

Once these four alerts have been selected, click OK.

- 8 .  The four alerts are listed in the Manage Alert Groups window.

Click Save to save the new alert group.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 9 .  View the result window and click OK.

- 10 . Click the Actions menu button and select Manage Notifications.

This initiates the process of creating a new notification.

The Manage Alert Notifications window opens.

- 11 . Click the plus (+) button.

The Create Alert Notification window opens.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 12 . In the Create Alert Notification window, make the following selections.

Name: HDFS Storage Operators

Groups: Select the Custom radio button and then select HDFS Storage Alerts

Severity: WARNING and CRITICAL (use the Shift key to select multiple levels)

Description: Notification configuration for HDFS storage operators.

Method: EMAIL

Email To: hdfsstorageops@somecompany.com

SMTP Server: smtp.somecompany.com

SMTP Port: 25

Email From: ambarialerts@somecompany.com

Use authentication: select it

Username: admin

Password: cangetin

Password Confirmation: cangetin

Start TLS: select it

Then click Save to create the notification.

No email server is available in the lab environment so no actual email will be sent.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

- 13 . The result is displayed in the Manage Alert Notifications window.

Click Close.

- 14 . Click the Actions menu button again and select Manage Alert Groups.

- 15 . Select the HDFS Storage Alerts group.

Notice that the HDFS Storage Operators notification has been assigned to the alert group.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing Ambari Alerts

There is nothing to change so click Cancel.

- Result

- You have now:

- Listed alert definitions; disabled, enabled, and edited an alert definition; listed alert instances and

- triggered an alert; and created a new alert group and notification.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

- Lab: Managing HDFS Snapshots

- About This Lab

- Objective:

To use HDFS command-line utilities and NameNode UI to create andmanage HDFS snapshots

- File locations:

N/A

- Successful outcome:

You will: Enable an HDFS directory for snapshots and then create, view,rename and delete a snapshot.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Protecting a Cluster with Backups

- Enabling Snapshots

- Enable HDFS snapshots on the /user/root directory.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  Assume HDFS superuser permissions in order to enable HDFS snapshots.

- # su - hdfs

- 3 .  Use the dfsadmin command with the –allowSnapshot option to enable snapshots on the

/user/root directory.

When you are finished, use the lsSnapshottableDir command to view the list of snapshottableHDFS directories.

- $ hdfs dfsadmin -allowSnapshot /user/root

- $ hdfs lsSnapshottableDir

- 4 .  Assume normal root user permissions again.

- $ exit

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Managing HDFS Snapshots

- Managing Snapshots

- Create, view, rename, explore, and delete an HDFS snapshot.

- 1 .  Use the HDFS Shell –ls command to determine if there are any HDFS snapshots

on the /user/root directory.

- # hdfs dfs -ls /user/root/.snapshot

There should not be any snapshots.

- 2 .  Create an HDFS snapshot of the /user/root directory using the HDFS Shell –createSnapshot

command.

- # hdfs dfs -createSnapshot /user/root

Notice that you did not use the command option to explicitly name the snapshot,

so HDFS assigned the snapshot a default name. The default name is based on the current dateand time.

- 3 .  Use the HDFS Shell –ls command again to determine if there are any HDFS snapshots on the

/user/root directory.

- # hdfs dfs -ls /user/root/.snapshot

You should see a snapshot listed.

- 4 .  Use the HDFS Shell –renameSnapshot command to rename the /user/root snapshot.

Replace the variable name in the command below with your actual snapshot name.

- # hdfs dfs -renameSnapshot /user/root s<yyyymmdd-hhmmss.sss> mysnap

You should not see any output from the command.

- 5 .  Use the HDFS Shell –ls command again to determine if the snapshot was renamed.

- # hdfs dfs -ls /user/root/.snapshot

You should see the new mysnap snapshot name.

- 6 .  Use the HDFS Shell –ls command to display the contents of the snapshot directory mysnap.

Also use the –ls command to display the contents of the /user/root directory.

How do they compare?

- # hdfs dfs -ls .snapshot/mysnap

- # hdfs dfs -ls /user/root

The two directories should have identical content.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Managing HDFS Snapshots

- 7 .  Use the HDFS Shell –put command to upload the local file /root/wordcount.jar to the

HDFS /user/root directory.

- # hdfs dfs -put /root/labs/wordcount.jar /user/root

You should see no output from this command.

- 8 .  Use the HDFS Shell –ls command to display the contents of the snapshot directory mysnap.

Also use the –ls command to display the contents of the /user/root directory.

How do they compare?

- # hdfs dfs -ls .snapshot/mysnap

- # hdfs dfs -ls /user/root

The wordcount.jar file is present only in the /user/root directory.

The wordcount.jar file should not be present in the mysnap snapshot.

- 9 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 10 . Log in to the Ambari Web UI using the user name admin and the password admin.

- 11 . Click Services and select HDFS.

- 12 . Click Quick Links.

Select the active NameNode system, and then select NameNode UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Managing HDFS Snapshots

The NameNode UI opens in a new browser tab.

- 13 . Click Snapshot to view HDFS snapshot information on the Snapshot page.

How many snapshottable directories are there?

Which directory is snapshottable?

Are there any current snapshots?

What is the name of the current snapshot?

- 14 . Move back to the terminal window that is logged in to node1.

- 15 . Use the HDFS Shell command –deleteSnapshot to delete the mysnap snapshot. Then verify

that the snapshot has been removed.

- # hdfs dfs -deleteSnapshot /user/root mysnap

- # hdfs dfs -ls /user/root/.snapshot

The snapshot should be gone.

- Result

- You have now:

- Enabled an HDFS directory for snapshots and then created, viewed, renamed and deleted a snapshot.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

- Lab: Using DistCp

- About This Lab

- Objective:

To use the DistCp command and options to copy HDFS files anddirectories

- File locations:

N/A

- Successful outcome:

You will: View online manual information for the distcp command;configure a DistCp test environment; and copy files and directories usingthe distcp command and options.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Protecting a Cluster with Backups

- Viewing Online DistCp Information

- View the online manual information for the distcp command.

- 1 .  Open a terminal window on the Ubuntu desktop.

(Look for the terminal icon on the desktop)

Use SSH to log in to node1.

- # ssh node1

- 2 .  View the online manual page for distcp.

- # hadoop distcp -help

- Configuring a DistCp test environment.

- Configure a DistCp test environment on your single node cluster

- NOTE:

- Because there is only a single Hadoop cluster in the lab environment, this  lab will simulate copying files

- and directories from one cluster to another by using remote cluster copy syntax to copy files within a

- single cluster.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Using DistCp

- 1 .  Use the HDFS Shell –put command to upload the file /root/labs/salaries.txt to the

HDFS /user/root directory.

Then verify that the file has been uploaded.

- # hdfs dfs -put /root/labs/salaries.txt

- # hdfs dfs -ls

- 2 .  Use the HDFS Shell –mkdir command to create an HDFS source directory named

/user/root/sourcedir.

Then verify that the directory was created.

- # hdfs dfs -mkdir sourcedir

- # hdfs dfs -ls

- 3 .  Use the HDFS Shell –put command to upload the files /root/labs/test1.pig and

/root/labs/test2.pig to the HDFS /user/root/sourcedir directory.

Then verify that the files were uploaded.

- # hdfs dfs -put /root/labs/test1.pig /root/labs/test2.pig sourcedir

- # hdfs dfs -ls sourcedir

- 4 .  Use the HDFS Shell –mkdir command to create an HDFS target directory named

/user/root/targetdir.

Then verify that the directory was created.

- # hdfs dfs -mkdir targetdir

- # hdfs dfs -ls

- 5 .  Use the HDFS Shell –mkdir command to create a second HDFS target directory named

/user/root/targetdir2.

Then verify that the directory was created.

- # hdfs dfs -mkdir targetdir2

- # hdfs dfs -ls

- 6 .  In the terminal window, use SSH to log in to the node2 system.

- # ssh node2

- 7 .  Verify that node2 can read HDFS data.

- # hdfs dfs -ls hdfs://node1:8020

If you received the message  “Operation category READ is not supported in state standby”then node1 is functioning as a Standby NameNode.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using DistCp

Repeat the command again but use node2 instead because it is functioning as the ActiveNameNode.

- # hdfs dfs -ls hdfs://node2:8020

The HDFS /user/root directory should be listed.

Continue to use whichever node produced the directory listing for the remainder of the labexercise.

The example commands will use node2.

- Copying Files and Directories

- Copy files and directories to another HDFS directory using DistCp and DistCp options.

- 1 .  Copy the /user/root/salaries.txt file to the /user/root/targetdir directory using the

distcp command.

Then verify that the file was copied.

- # hadoop distcp hdfs://node2:8020/user/root/salaries.txt

- hdfs://node2:8020/user/root/targetdir

- # hdfs dfs -ls targetdir

There should be a salaries.txt file in targetdir.

- 2 .  Use the HDFS Shell –ls command to list the contents of the

/user/root/targetdir/sourcedir directory.

- # hdfs dfs -ls targetdir/sourcedir

You should see the test1.pig and test2.pig files.

Notice that when copying directories with DistCp, the default behavior is to copy the sourcedirectory and its files to the target directory.

- 3 .  Copy the /user/root/sourcedir directory again, but this time copy it to the

/user/root/targetdir2 directory.

Then verify that the sourcedir directory and its two files were copied.

- # hadoop distcp hdfs://node2:8020/user/root/sourcedir

- hdfs://node2:8020/user/root/targetdir2

- # hdfs dfs -ls targetdir2

- # hdfs dfs -ls targetdir2/sourcedir

You should see the sourcedir directory in the targetdir2 directory.

You should also see the test1.pig and test2.pig files in the sourcedir directory.Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Using DistCp

- 4 .  Use the HDFS Shell –rm –R command to remove the sourcedir directory from the

targetdir2 directory.

- # hdfs dfs -rm -R targetdir2/sourcedir

- # hdfs dfs -ls targetdir2

The targetdir2 directory should be empty.

- 5 .  Again, copy the /user/root/sourcedir directory to the /user/root/targetdir2

directory but this time add the –update option.

List the contents of the targetdir2 directory when the distcp command has finished.- # hadoop distcp -update hdfs://node2:8020/user/root/sourcedir

- hdfs://node2:8020/user/root/targetdir2

- # hdfs dfs -ls targetdir2

With the addition of the –update option, the test1.pig and test2.pig files were copieddirectly into the targetdir2 directory. The sourcedir directory was not copied.

This same behavior will be seen when the –overwrite option is used.

- 6 .  Again, copy the /user/root/sourcedir directory to the /user/root/targetdir2

directory but this time add the –overwrite option.

List the contents of the targetdir2 directory when the distcp command has finished.- # hadoop distcp -overwrite hdfs://node2:8020/user/root/sourcedir

- hdfs://node2:8020/user/root/targetdir2

- # hdfs dfs -ls targetdir2

With the addition of the –overwrite option, the test1.pig and test2.pig files were copieddirectly into the targetdir2 directory again. They were copied even though they had notchanged.

Once again, the sourcedir directory was not copied because the –overwrite option was used.- Result

- You have now:

- Viewed online manual information for the distcp command; configured a DistCp test environment; and

- copied files and directories using the distcp command and options.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

- Lab: Installing HDP

- About This Lab

- Objective:

To interactively install a single-node HDP cluster using the Ambari Web UI- File locations:

N/A

- Successful outcome:

You will: Reset your lab environment; install, configure, and start theAmbari Server; and perform an interactive HDP installation using theAMbari Web UI.

- Before you begin

Start and connect to your classroom lab environment

- Related lesson:

Installing the Hortonworks Data Platform

- Resetting the Lab Environment

- Reset your lab environment.

- 1 .  Open a terminal window on the Ubuntu desktop (look for the terminal icon on the desktop).

- 2 .  On the Ubuntu desktop (not the node1 desktop), run the admin_course.sh script.

- # cd /root/.sys

- # ./admin_course.sh

The command will reset the Docker environment, producing four pristine nodes. Node1 can beused to complete this installation lab.

- Installing Ambari Server

- Install, configure, and start the Ambari Server.

- 1 .  In the terminal window, use SSH to log into node1.

- # ssh node1

When asked by SSH if you want to continue connecting, type yes.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Installing HDP

- 2 .  To complete some of the pre-installation setup, change directory to the /root/scripts

directory.

Verify that the current directory is /root/scripts.

- # cd  /root/scripts

- # pwd

The pwd command should report that the current directory is /root/scripts.

- 3 .  On the node1 system, you may view and then run the env_setup.sh script.

This script prepares the CentOS cluster nodes for an HDP cluster installation.

The main functions in this script are to move a pre-downloaded ambari.repo file to thecorrect location,

finish creating a local HDP software repository on node1 that will be used to install the HDPsoftware,

and configure password-less SSH connections between the CentOS cluster nodes.

Password-less SSH connections enable the automatic installation and registration of Ambariagents on the cluster nodes.

The script also turns off the Linux firewall.

- (optional) # more env_setup.sh

- # ./env_setup.sh

You should see a lot of screen output as the script runs.

- 4 .  While still on the node1 system, use the yum command to install the Ambari Server software.

- # yum -y install ambari-server

You should see the Ambari Server software being downloaded and installed.

- 5 .  When the Ambari Server is first initialized, the Ambari Server software checks for the presence

of Java software.

If the Java software ZIP and GZIP files have been manually downloaded to the

/var/lib/ambari-server/resources directory,

Ambari installs Java from there. Otherwise it downloads and installs Java from the Internet.For greater installation speed and convenience, the lab virtual machine has already dlowloadedJava 1.8.

Run the copy_jdk.sh script to copy the downloaded Java software to the /var/lib/ambari-server/resources directory.

- # ./copy_jdk.sh

The script completes very quickly and produces no screen output.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im0](images/Im0)

Lab: Installing HDP

- 6 .  The Ambari Server must be initialized before it can be started.

Initialize the Ambari Server by running the ambari-server setup -s command.

The –s option is the “silent” option which causes Ambari to install with default settings.- # ambari-server setup -s

Watch the screen output.

It should perform such actions as installing the JDK software and initializing and starting theAmbari database.

- 7 .  Once the Ambari Server has been initialized, start the Ambari Server.

- # ambari-server start

Watch the screen output.

You should see the Ambari Server starting and also see a “successful” message.

- 8 .  You may leave the terminal window open, but you are finished using it for now.

- Installing HDP

- Perform an interactive HDP installation using the Ambari Web UI

- 1 .  Open the Firefox browser on the Ubuntu desktop and connect to the Ambari Server at the URL

http://node1:8080.

- 2 .  Log in to the Ambari Web UI using the user name admin and the password admin.

- 3 .  Because the Ambari Server cannot find an installed cluster,

it presents the option to install a cluster.

Click Launch Install Wizard.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Installing HDP

- 4 .  Type horton as the cluster name and click Next.

- 5 .  Ensure that only the HDP 2.3 radio button is selected.

Then click Advanced Repository Options.

- 6 .  Deselect all check boxes except for redhat6.

Then edit the Base URLs for the redhat6 HDP 2.3 and HDP-UTILS-1.1.0.20 software

repositories. The URLs should direct the installer program to the local software repositoriesthat have been set up on the node1 system.

The HDP-2.3 URL should be http://node1/hdp/HDP-2.3.

The HDP-UTILS-1.1.0.20 URL should be http://node1/hdp/HDP-UTILS-1.1.0.20.Then click Next.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Installing HDP

- 7 .  Type node1 as the target host.

NOTE

Because of the unique classroom lab environment a fully qualified domain name is notnecessary. However, in most “real world” cluster installations, a fully qualified domain name isrequired for proper installation and cluster operation.

You are installing only a single cluster node now to reduce installation time in the lab exercise.A single node also reduces the number of required hardware resources. It is possible to addmultiple target hosts, one per line.

- 8 .  In the same installation window, click Browse to locate the password-less SSH private key file

that is required for automated Ambari agent installation and registration.

- 9 .

Locate the training-keypair.pem file and Open it.

It is located on the Ubuntu Desktop.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Installing HDP

- 10 . Click Register and Confirm to install and register the Ambari agent on node1.

If multiple nodes had been entered, the agent would be installed and registered

on all of the nodes that were entered.

- 11 . Because of the normal requirement of using fully qualified domain names,

you will get a Warning window about not using FQDNs.

Click OK to dismiss the window and continue.

- 12 . Monitor the agent installation progress window.

The agent is installed and registered and then a series of system checks are performedon the nodes to be installed (only node1 in your lab environment).

You will receive a few warnings but these can be ignored in the lab environment.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Installing HDP

Click Next to continue the installation.

- 13 . A Confirmation window opens and warns that some of the host checks failed.

The failures are minor in the lab environment and will not cause problems.

Click OK to dismiss the window and continue the installation.

- 14 . Next, choose which cluster services to install.

To reduce installation time in lab and to minimize the lab environment hardware

requirements, you will only install a few of the available services.

Ensure that only HDFS, YARN + MapReduce2, Tez, Hive, Pig, ZooKeeper, andAmbari Metrics are selected.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Installing HDP

Then click Next.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Installing HDP

- 15 . The Assign Masters window is where you would choose which cluster nodes would

run which master service components.

The purpose of this step is to evenly balance the master services’ workloads across multiplesystems.

In the lab environment there is only a single node so there are no master services to move atthis time.

View the window and click Next to continue.

- 16 . The Assign Slaves and Clients window is where you would choose which cluster nodes

will run which worker processes.

Worker processes perform most of the data processing in a cluster.

The more nodes that you have running worker processes, the more work that can be

simultaneously accomplished. In the lab environment there is only a single node so are noworker processes to move at this time.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

Lab: Installing HDP

View the window and click Next to continue.

- 17 . The Customize Services window enables you to configure or customize cluster service

property settings during installation.

If there are any property settings that must be configured prior to installation,

they are noted by red-colored alert icons.

Notice that there is an alert icon next to Hive.

Click Hive to open the Hive page.

- 18 . Notice that there is an alert icon on the Hive Advanced tab.

Click the Advanced tab.

- 19 . Scroll down in the window until you find the Database Password property.

Notice that it is displayed in red. Type and retype hive as the database password.

The red lettering will switch to black lettering once the password has been accepted.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im4](images/Im4)

![Im0](images/Im0)

Lab: Installing HDP

- 20 . Because there are no more alerts to process,

Scroll down in the window and click Next to continue.

- 21 . Review your selections for accuracy and then click Deploy.

- 22 . Monitor the installation progress.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im3](images/Im3)

![Im0](images/Im0)

Lab: Installing HDP

- 23 . When the progress window indicates that the installation has completed, click Next.

- 24 . Read the Summary window and click Complete.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im2](images/Im2)

![Im0](images/Im0)

Lab: Installing HDP

- 25 . After completing the installation, the Ambari Web UI dashboard is displayed.

- Result

- You have now:

- Reset your lab environment; installed, configured, and started the Ambari Server; and performed an

- interactive HDP installation using the AMbari Web UI.

Copyright © 2012 - 2016 Hortonworks, Inc. All rights reserved.

![Im1](images/Im1)

![Im0](images/Im0)

![Im0](images/Im0)

![Im1](images/Im1)

![Im0](images/Im0)

Hortonworks University courses are designed by the leaders and committers of Apache Hadoop.We  provide immersive, real-world experience in scenario-based training. Courses offer

unmatched depth and expertise available in both the classroom or online from anywhere in theworld. We prepare you to be an expert with highly valued skills and for Certification.

