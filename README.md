# Quick Start Guide

## [ownCloud][]

## Installing and connecting to an ownCloud server.

##### 0.1

##### Ray Brett

### Introduction
Sharing of files in synchronised folders across multiple devices, including mobile, is made possible by ownCloud.

This guide is an ownCloud "Hello World" showing how to quickly install an ownCloud server, configure it via an administrator client and connect to it from a local user client.

### Prerequisites
The following were used for this guide but [many][Downloads] hypervisors and platforms are also supported:

- ownCloud 10.0.10 server virtual machine ([appliance][Downloads]) for VirtualBox
- ownCloud Desktop [client][Downloads] for Ubuntu 18.04LTS
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) 5.2
- [Ubuntu 18.04LTS](https://www.ubuntu.com/download) for both VirtualBox and the ownCloud Desktop client

### &#9888; Warning
Mobile and off-intranet clients would require the server to be reachable from the internet requiring network and security-hardening expertise and permissions to minimise security risks and are beyond the scope of this guide. See the [Admin Manual][] and the [latest supplementary admin manual][] for more information on possible risks and mitigation.

### Install an ownCloud server
1. Locate the ownCloud server appliance on https://owncloud.org/download/ and download the VirtualBox image.
2. Import the image file into VirtualBox: **File> Import Appliance...**.
3. Start the imported virtual machine (VM): **Start**.
4. Step through the Configuration Wizard in the VM window that appears.  
<img src="images/vm2 domain and network.png" title="Domain and Network Configuration screen of VM Configuration Wizard" alt="Domain and Network Configuration screen of VM Configuration Wizard" align="center" width="500"/>  
5. If necessary, modify the default values on the Domain and Network Configuration screen, e.g. by manually setting the IP address.  
<img src="images/vm3 domain.png" title="Domain Configuration screen of VM Configuration Wizard" alt="Domain Configuration screen of VM Configuration Wizard" align="center" width="500"/>  
6. Specify the default "Manage users and permissions directly on this system" on the Domain Configuration screen of VM Configuration Wizard.  
<img src="images/vm4 account.png" title="Account Configuration screen of VM Configuration Wizard" alt="Account Configuration screen of VM Configuration Wizard" align="center" width="500"/>  
7. Enter the email address to which the license is to be sent on the Account Configuration screen of VM Configuration Wizard.  
<img src="images/vm5 host settings.png" title="Host Settings Configuration screen of VM Configuration Wizard" alt="Host Settings Configuration screen of VM Configuration Wizard" align="center" width="500"/>  
8. Review the Host Settings Configuration screen of VM Configuration Wizard.  
<img src="images/vm6 confirm configuration settings.png" title="Confirm Configuration Settings screen of VM Configuration Wizard" alt="Confirm Configuration Settings screen of VM Configuration Wizard" align="center" width="500"/>  
9. Review the Configuration Settings screen of VM Configuration Wizard, ensuring that **Update system after setup** is ticked.
10. If correct, click **Configure System** to proceed. This may take some time to complete.  
<img src="images/vm8 setup successful.png" title="Setup successful screen of VM Configuration Wizard" alt="Setup successfuls screen of VM Configuration Wizard" align="center" width="500"/>  
11. Click **Finish** on the Setup Successful screen.  
<img src="images/vm9 final screen with URL for Admin client.png" title="ownCloud Appliance screen of VM Configuration Wizard" alt="ownCloud Appliance screen of VM Configuration Wizard" align="center" width="500"/>  
12. *Before* clicking on the final ownCloud Appliance screen, open a browser and navigate to the IP address displayed.  
13. After clicking on the final ownCloud Appliance screen, press any key to open a text console and then login to the ownCloud server as root using the password you defined earlier.  
14. Stop the rpcbind service to prevent a security exploit of it by executing the following commands:  
```  
service --status-all | grep rpcbind  
service rpcbind stop  
service --status-all | grep rpcbind  
```  

### Configure the ownCloud server via the administrator client

#### Connect the Administrator client
1. Open a browser at the IP address of the ownCloud server that was displayed on the openCloud VM screen.
2. Enter an email address, when prompted, to which a license file will be sent.
3. Click **Request Activation**.  
An email with a license file will be sent to the email address you configured.
4. Follow the instructions on the next screen to upload the license file.
5. Click **Finish** on the Activation success screen to open a welcome screen.
6. Click on the **X** to close the welcome screen and get to the Univention Portal screen.  
<img src="images/univention portal.png" title="Univention Portal screen" alt="Univention Portal screen" align="center" width="500"/>  
7. This screen has links for both the administrator and user web clients. 
8. Click on **System and domain settings** to open a login screen for the administrator web client.
9. Enter "Administrator" and the root password you defined to access the administrator web client below.  
<img src="images/admin client home screen.png" title="admin client home screen" alt="admin client home screen" align="center" width="500"/>  

#### Add a user
1. Browse to the Administrator client by entering the IP address of the ownCloud server and then clicking on **System and domain settings**.
2. If prompted, enter "Administrator" and the root password you defined.
3. On the Administrator client, click on **Users**.
4. Click **New**.
5. Enter a Username and Last name then click Next.
6. Enter a password then click **Create User**.

### Connect a User client to the ownCloud server

The ownCloud user manual is located [here][user manual].

#### User web client
1. Browse to a User web client by entering the IP address of the ownCloud server and clicking on ownCloud.
2. Login as the user you added.
3. Explore the functionality.

#### User desktop client
1. Download a Desktop client, e.g. the production Destop client for Linux, from [downloads][].
2. Click **OK** on a distribution filtering dialog if it appears.
3. Select your operating system, e.g. **Ubuntu**, and click on it.
4. Click on **Add repository and install manually**.
5. For Ubuntu 18.04, execute the commands to add the repository key shown under **"You can add the repository key to apt..."**.
6. Execute the commands to add the repository, update and to install owncloud-client shown under **"For Ubuntu 18.04..."**.
7. Launch the ownCloud Destop client.
8. If prompted, enter the ownCloud server IP address.
9. You may be asked to trust the self-generated certificate.  
<img src="images/desktop client login.png" title="desktop client login" alt="desktop client login" align="center" width="500"/>  
10. Enter the username and password for the user you added and click **Next**.  
<img src="images/desktop client options.png" title="desktop client options" alt="desktop client options" align="center" width="500"/>  
11. Click **Connect...** on the next screen and explore the home screen below.  
<img src="images/desktop client home.png" title="desktop client home" alt="desktop client home" align="center" width="500"/>  

#### Mobile client
The IOS app user guide is [here](https://doc.owncloud.org/ios/index.html).  
The Android app user guide is [here](https://doc.owncloud.org/android/index.html).

#### &#9888; Warning  
Mobile and off-intranet clients would require the server to be reachable from the internet requiring network and security-hardening expertise and permissions to minimise security risks and are beyond the scope of this guide. See the [Admin Manual][] and the [latest supplementary admin manual][] for more information on possible risks and mitigation.

1. Search for "ownCloud" on the Apple or Google App store or download them from [downloads][].
2. When you install an ownCloud app and open it you will be prompted for your ownCloud server URL and ownCloud user login credentials.  
When the app connects it opens to the user's Files page.

### Useful Links
[ownCloud][].  
[Community][].  
[Downloads][].  
[Admin manual][].  
[Latest supplementary admin manual][].  
[User manual][].  
[Latest supplementary user manual][].  
[IOS app user guide][ios].  
[Android app user guide][android].  

  [ownCloud]: 			https://owncloud.org/							"ownCloud"
  [Downloads]: 			https://owncloud.org/download/						"ownCloud downloads"
  [Admin manual]: 		https://doc.owncloud.org/server/administration_manual/index.html	"admin manual"
  [Latest supplementary Admin manual]: https://doc.owncloud.org/server/latest/admin_manual/		"latest supplementary admin manual"
  [User manual]: 		https://doc.owncloud.org/server/user_manual/index.html			"user manual"
  [Latest supplementary User manual]: 	https://doc.owncloud.org/server/latest/user_manual/ 		"latest supplementary user manual"
  [ios]: 			https://doc.owncloud.org/ios/index.html					"ios user guide"
  [android]: 			https://doc.owncloud.org/android/index.html				"android user guide"
  [Community]: 			https://owncloud.org/community/						"community"


