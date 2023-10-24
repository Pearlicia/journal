1. Your company employs the use of a virtual desktop infrastructure for it employees which consists of a thin client that provisions a windows desktop environment from a centralised server. Based on this scenario, which of the following best describes this client server architecture?
A. The client workstations distribute shared resources including memory, processor, and network interfaces
B. The client workstations contain minimal resources necessary to render the workspace
C. The client workstations fulfil the resources requests made by other client workstations
D. The client workstations are likely headless and have no user interface or utilize peripheral devices

#### Answer
The best answer is **B. The client workstations contain minimal resources necessary to render the workspace**.

In a VDI client-server architecture, the client workstations are typically thin clients or zero clients, which are devices that have minimal hardware resources, such as a CPU, memory, and storage. The client workstations rely on the centralized server to provide the virtual desktops and to render the graphical user interface.

The other answer choices are incorrect:

* **A. The client workstations distribute shared resources including memory, processor, and network interfaces:** This is not a typical characteristic of a VDI client-server architecture. In a VDI environment, the client workstations are typically not responsible for distributing shared resources.
* **C. The client workstations fulfil the resources requests made by other client workstations:** This is not a typical characteristic of a VDI client-server architecture. In a VDI environment, the client workstations typically only request resources from the centralized server.
* **D. The client workstations are likely headless and have no user interface or utilize peripheral devices:** This is not always the case. Some thin clients do have a user interface and can support peripheral devices. However, it is true that many thin clients are headless, meaning that they do not have a display or any other input devices.

In your scenario, the thin client provisions a Windows desktop environment from a centralized server. This means that the client workstation is responsible for rendering the Windows desktop and displaying it to the user. Therefore, the client workstation must have at least the minimal resources necessary to do this.

Here is a diagram of a typical VDI client-server architecture:

[Diagram of a VDI client-server architecture]

As you can see, the client workstations are thin clients that connect to the centralized server over a network. The centralized server hosts the virtual desktops and renders the graphical user interface. The client workstations only need to have the minimal resources necessary to render the workspace and transmit user input to the server.


2. Hackers and cybercriminals are creating fake offers to steal money, creating phishing pages and leveraging technology tools. That said, a security manager of an organisation will constantly issue reminders about cyber safety, password security, and computer security. What are the elements the security manager would include in his company hacker/cybercriminal reminder emails? Select the best answer 
A. Stolen data from data breaches are sold on the dark Web wherein hackers can purchase the data through  valid login credentials 
B. During attacks, hackers overload the servers of websites; thus rendering all servers unfunctional 
C. A malicious code or malicious script is sent to a website or Web application through channels intended for data
D. Avoid unknown emails, avoid unknown links, use strong password protection, connect to secure WiFi, enable firewall  protection and back up files

#### Answer

The best answer is **D. Avoid unknown emails, avoid unknown links, use strong password protection, connect to secure WiFi, enable firewall protection and back up files**.

These are all important security tips that can help to protect users from hackers and cybercriminals.

The other answer choices are incorrect:

* **A. Stolen data from data breaches are sold on the dark Web wherein hackers can purchase the data through valid login credentials:** This is true, but it is not something that users can do much about to protect themselves. The security manager is more likely to focus on things that users can do to protect themselves, such as using strong passwords and avoiding phishing emails.
* **B. During attacks, hackers overload the servers of websites; thus rendering all servers unfunctional:** This is also true, but it is something that the security manager is more likely to be concerned with than the users. The security manager is responsible for putting in place measures to protect the company's systems from denial-of-service attacks.
* **C. A malicious code or malicious script is sent to a website or Web application through channels intended for data:** This is a type of attack that is known as a cross-site scripting (XSS) attack. Again, this is something that the security manager is more likely to be concerned with than the users. The security manager is responsible for putting in place measures to protect the company's website from XSS attacks.

The security manager's goal is to educate users about the latest cyber threats and to provide them with tips on how to protect themselves. By including the elements in answer choice D in his reminder emails, the security manager can help to keep his company's users safe from hackers and cybercriminals.


3. When creating a checklist of the physical security in an office, which of the following answer choices best represents the items that should be included?
A. Physical security measures, controlled access 
B. Login credentials, authorisation 
C. Authentication, firewall updates
D. Update of access policies, controlled access

#### Answer
The best answer is **A. Physical security measures, controlled access**.

Physical security measures are designed to protect a physical location and its occupants from unauthorized access, damage, or theft. Controlled access is a physical security measure that restricts who can enter or exit a building or area.

The other answer choices are incorrect:

* **B. Login credentials, authorisation:** Login credentials and authorization are more related to cybersecurity than physical security.
* **C. Authentication, firewall updates:** Authentication and firewall updates are also more related to cybersecurity than physical security.
* **D. Update of access policies, controlled access:** Updating access policies is a good way to improve controlled access, but it is not the only item that should be included on a checklist of physical security in an office.

Here is a sample checklist of physical security items that should be included in an office:

* **Physical security measures:**
    * Doors and windows are locked when not in use
    * Security cameras are installed and operational
    * Access control system is in place
    * Perimeter security measures are in place (e.g., fence, gate, security guards)
* **Controlled access:**
    * Visitor management system is in place
    * Employees are issued badges or other identification
    * Employees are trained on security procedures
* **Other:**
    * Fire extinguishers and other emergency equipment are properly maintained
    * Emergency evacuation plan is in place and employees are trained on it
    * Office is well-lit and free of clutter

This is just a sample checklist, and the specific items that should be included will vary depending on the specific office environment and security needs.


4. 
Which of the following options allow a user to view the ip addresses of their machine from their Linux terminal 
A. Hostname
B. ifconfig 
C. ipconfig 
D. curl ident.me

#### Answer
The best answer is **B. ifconfig**.

The `ifconfig` command is a Linux command that is used to display information about network interfaces. It can be used to view the IP addresses of all network interfaces on the machine, as well as other information such as the MAC address, link status, and MTU.

The other answer choices are incorrect:

* **A. Hostname:** The `hostname` command is used to display the hostname of the machine. It does not display the IP addresses of the network interfaces.
* **C. ipconfig:** The `ipconfig` command is a Windows command that is used to display information about network interfaces. It is not available on Linux.
* **D. curl ident.me:** The `curl ident.me` command can be used to view the public IP address of the machine. However, it cannot be used to view the IP addresses of the network interfaces.

To view the IP addresses of your machine from your Linux terminal, you can use the following command:

```
ifconfig
```

This will display a list of all network interfaces on the machine, along with their IP addresses. For example, the following output shows that the machine has two network interfaces, `eth0` and `lo`, with the IP addresses 192.168.1.100 and 127.0.0.1, respectively:

```
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:112989 (112.9 KB)  TX bytes:99693 (99.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7968 (7.9 KB)  TX bytes:7968 (7.9 KB)
```

5. As a security application what does an intrusion detection system do?

#### Answer
An intrusion detection system (IDS) is a security application that monitors network traffic for suspicious activity. It can detect both known and unknown threats, and it can alert security personnel when it detects a potential attack.

IDSs work by analyzing network traffic for patterns that are associated with malicious activity. For example, an IDS might look for traffic that is coming from known malicious IP addresses, or it might look for traffic that is using known attack vectors.

IDSs can be deployed in a variety of ways, including:

* **Network-based IDS (NIDS):** A NIDS is deployed at a strategic point on the network, such as the firewall or the gateway. It monitors all traffic that enters or leaves the network.
* **Host-based IDS (HIDS):** A HIDS is installed on individual hosts, such as servers and workstations. It monitors traffic that is generated by or destined for the host.
* **Hybrid IDS:** A hybrid IDS combines the features of a NIDS and a HIDS. It monitors traffic at both the network and host levels.

IDSs are an important part of any layered security posture. They can help to detect and respond to threats before they cause damage.

Here are some examples of what an IDS can do:

* Detect unauthorized access to the network
* Detect malware infections
* Detect denial-of-service attacks
* Detect data breaches
* Detect malicious insider activity

IDSs can also be used to monitor compliance with security policies. For example, an IDS can be used to detect traffic that is violating a firewall policy or to detect users who are accessing unauthorized websites.

IDSs are an essential tool for any organization that wants to protect its network and data from cyberattacks.

6. When an email is received with a suspicious link what's the name of the attack
A. Reconnaissance attack
B. Worm attack
C. Malware attack 
D. Phishing attack

#### Answer
The best answer is **D. Phishing attack**.

A phishing attack is a type of cyberattack where the attacker sends fraudulent emails or text messages that appear to be from a legitimate source. The attacker's goal is to trick the victim into clicking on a malicious link or opening an attachment, which can then install malware on the victim's device or steal their personal information.

The other answer choices are incorrect:

* **A. Reconnaissance attack:** A reconnaissance attack is the first phase of a cyberattack where the attacker gathers information about the target. This information can be used to plan and execute the attack.
* **B. Worm attack:** A worm attack is a type of malware that can self-propagate through a network. Worms typically exploit vulnerabilities in software or operating systems to spread.
* **C. Malware attack:** Malware is malicious software that can damage or disable a computer system or steal data. Malware can be spread through a variety of ways, including phishing attacks, email attachments, and drive-by downloads.

Phishing attacks are a common type of cyberattack, and they are becoming increasingly sophisticated. It is important to be aware of the signs of a phishing attack and to avoid clicking on links or opening attachments from unknown senders.

Here are some tips for avoiding phishing attacks:

* Be wary of emails from unknown senders.
* Do not click on links in emails unless you are sure the link is legitimate.
* Do not open attachments from unknown senders.
* Keep your software and operating systems up to date.
* Use a strong password manager and create unique passwords for all of your online accounts.
* Enable two-factor authentication on all of your online accounts.

If you think you may have been the victim of a phishing attack, you should immediately change your passwords and contact your bank or credit card company to report any fraudulent activity.

7. Which choice  best describes the three types of controls used to maintain a network security
A. Physical, Technical and Administrative 
B. Authentication, Authorisation, and Location
C. Hardware, Software and users
D. Administrative, Hardware and software 

#### Answer
The most accurate choice describing the three types of controls used to maintain network security is:

A. Physical, Technical, and Administrative

These are commonly recognized categories of controls in the field of information security and network security:

Physical Controls: These controls focus on the physical aspects of security, such as access to data centers, facilities, and equipment. Examples include security cameras, locks, and biometric access systems.

Technical Controls: Technical controls encompass hardware and software solutions that help secure a network. This includes firewalls, intrusion detection systems, encryption, and access control lists.

Administrative Controls: Administrative controls are the policies, procedures, and guidelines set by an organization to manage and govern its security practices. Examples include security policies, access management procedures, and security awareness training.

Option A accurately represents these key categories of controls used in network security.

8. Which command will display all open ports on a Linux os
A. ipconfig /all -alt
B. if config- a
C. Netstat -lntu 
D. ssh root@localhost "open"

#### Answer
The command that will display all open ports on a Linux operating system is:

C. netstat -lntu

This command, when executed in the terminal, will list all open (listening) ports on the system along with their respective protocols and addresses.


9. A malicious actor sends a spear phishing email to an innocent user of a business entity, which, clicked open, activates the account to execute a server message  block (SMB) authentication with a server infected with malicious programs and reveals user credentials. Which of the following four elements of a risk scenario should be  included in a risk assessment report
A. Integrity, authenticity, discovery and exploitation 
B. Confidentiality, integrity, enumeration and whaling 
C. Threat event, vulnerabilities, asset, and consequences 
D. Non rebuttal, Confidentiality, threat event, and availability 

#### Answer
The four elements of a risk scenario that should be included in a risk assessment report are typically:

C. Threat event, vulnerabilities, asset, and consequences

These elements are critical for understanding and assessing the risk associated with the described scenario. Here's why:

Threat Event: This describes the action taken by the malicious actor (spear phishing email), which is the starting point of the scenario. Understanding the threat event is crucial for identifying potential risks.

Vulnerabilities: In this scenario, the vulnerabilities would be the weaknesses in the system or user's behavior that allowed the malicious actor's attack to be successful. Identifying vulnerabilities is essential for risk assessment.

Asset: The asset in this case would be the sensitive user credentials and potentially other valuable data or resources that could be compromised. Knowing what is at risk is crucial for assessing the impact of a security breach.

Consequences: This element involves understanding the potential impact of the threat event exploiting the vulnerabilities. In this scenario, the consequences would involve data disclosure, potential unauthorized access, and other negative outcomes.

So, option C best represents the elements of a risk scenario that should be included in a risk assessment report.


10. Based on the scenario outlined below, which of the following best describes the client server architecture described in this scenario? You work for an online retailer that uses a proprietary intranet portal. When employees login, they are presented with a branded Web page containing links to company resources. The Web page also contains a widget that allows the user to enter sales transactions on your company's customer relationship management CRM system . The CRM writes inventory data into a MongoDB database that is hosted in a separate data center
A. Distributed cloud architecture 
B. Host server platform
C. Three tier applications 
D. Enterprise resource planning 

#### Answer
The scenario you described best fits the description of:

C. Three-tier architecture

In this scenario:

The client tier is represented by the employees who log in to the intranet portal using their web browsers.

The application tier is represented by the web server that serves the branded web page and contains the widget for entering sales transactions on the CRM system. The CRM system, in this case, acts as part of the application tier.

The data tier is represented by the MongoDB database hosted in a separate data center. This database stores the inventory data.

Three-tier architecture separates the application into three logical and separate tiers, which helps improve scalability, maintainability, and flexibility in such scenarios.


11. A team is learning about cloud computing, and they have decided to offload a large part of the creation and maintenance of the computing infrastructure to focus on their application  which type of service will best suit their needs?
A. Platform as a service
B. Application as a service 
C. Infrastructure as a service 
D. Software as a service 

#### Answer

For a team that wants to offload a large part of the creation and maintenance of the computing infrastructure to focus on their application, the best type of service is:

A. Platform as a service (PaaS)

PaaS provides a platform that includes infrastructure, runtime environment, and development tools, allowing developers to focus on building and deploying their applications without worrying about the underlying infrastructure details. This is ideal for teams looking to streamline application development and deployment while minimizing infrastructure management tasks.


12. You manage EweTube, a video streaming service for your for neighbour's sheep farm. The service includes its own mobile app which connects to your company's centralised server.  In its first week of going live, the site was bombarded by millions of viewers turning in to see the cute lambs. In response, you have decided it is time to scale the service. Based on this scenario, which of the following statements is the most accurate as you look to scale this centralised service 
A. To scale this service, you will need to add additional storage capacity and redundant disk arrays on the centralised servers
B. Because the service has been security hardened, load balancing is not necessary as the streaming site is not susceptible to denial of service incidents 
C. To scale this service, you may consider implementing a load balancer to prevent potential denial of service incidents 

#### Answer
The most accurate statement as you look to scale the centralized service in response to a sudden increase in viewers is:

C. To scale this service, you may consider implementing a load balancer to prevent potential denial of service incidents.

When you experience a sudden surge in viewers, load balancing can help distribute the incoming traffic across multiple servers to ensure the service remains available and responsive. It also provides redundancy, high availability, and helps protect against denial of service incidents. Adding additional storage capacity and redundant disk arrays (as mentioned in option A) might be necessary for scalability but doesn't directly address the issue of handling increased traffic and potential denial of service attacks. Additionally, while security hardening is important, it doesn't negate the need for load balancing when scaling a service to handle more users.


13. In an IaaS environment, the coud customer is responsible for which aspects of the architecture?
A. Performing software update on the application only
B. Launching but not maintaining the infrastructure 
C. Launching and maintaining the infrastructure and performing updates on application 
D. Deploying the application only

#### Answer
In an Infrastructure as a Service (IaaS) environment, the cloud customer is typically responsible for:

C. Launching and maintaining the infrastructure and performing updates on applications.

IaaS provides customers with virtualized computing resources, such as virtual machines, storage, and networking. While the cloud provider manages the underlying infrastructure, the customer is responsible for setting up, configuring, and maintaining the virtual machines and the applications running on them. This includes tasks like OS updates, application installations, and ongoing maintenance.


14. A team's application has had a services demand increase over the past couple of months; the team has not determined if this is a temporary spike or if the popularity of their application is growing sustainably. The chief financial officer has asked for an offset to these additional costs. Which statement is an option that will help the team find cost savings quickly ?
A. Enable notifications to be sent to the development team to approve additional services being spun up
B. Enable auto scaling with thresholds to meet the needs of the application and support a good user experience for the end users
C. Create a case with  the vendor's customer service team to discuss options 
D. Enable reserved capacity by agreeing to a 1 year commitment

#### Answer
To find cost savings quickly while dealing with an increase in service demand, the best option is:

D. Enable reserved capacity by agreeing to a 1-year commitment.

Enabling reserved capacity allows you to commit to using certain resources for a specified duration, typically 1 or 3 years, in exchange for reduced costs compared to on-demand pricing. This can provide cost savings in the medium to long term and is often a practical approach when you anticipate sustained growth in service demand. It's a strategic move to offset the additional costs while ensuring resource availability.


15. Which of the following answer choices represents an accurate representation of one of the building blocks of cloud computing.?
A. Virtual networks can provide systematic reviews of microservices offered in the cloud computing environments for high optimization 
B. Virtual networks can be configured as a standalone and then resources can be added based on application and organisational needs
C. Virtual networks can be configured as a monolithic application to provide sustainable, reliable and scalable services 
D. Virtual networks can provide easy migration from on prem to cloud based providers

#### Answer
The accurate representation of one of the building blocks of cloud computing is:

B. Virtual networks can be configured as a standalone, and then resources can be added based on application and organizational needs.

In cloud computing, virtual networks provide the foundational infrastructure for connecting resources and services. They can be configured independently and then used to connect various resources and services as needed. This flexibility is a key characteristic of cloud computing, allowing organizations to scale and adapt their network architecture to meet specific application and organizational requirements.