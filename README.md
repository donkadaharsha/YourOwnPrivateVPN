# YourOwnPrivateVPN
A secure, custom VPN setup on AWS using OpenVPN Server, providing private network access and enhanced privacy.

## Project Overview
This project demonstrates the creation of a private VPN using AWS and OpenVPN Server. By leveraging the flexibility and scalability of AWS, I configured a secure and customizable VPN environment that ensures enhanced privacy and control over network traffic. This setup allows for secure remote access to resources, bypassing geo-restrictions, and protecting online activities from third-party monitoring. The project includes detailed instructions on deploying the OpenVPN server on an EC2 instance, configuring security groups, and connecting client devices to the VPN.


## Why do you want to go through this process when you can just download pre built VPNs like Nord or Proton?
Creating your own VPN using AWS and OpenVPN offers several advantages over using a pre-built VPN service like NordVPN or ProtonVPN. However, there are also trade-offs to consider. Here's why - 
1. No Subscription Fees: Avoid ongoing subscription costs that come with commercial VPN services.
2. Trust Issues: You have to trust the VPN provider with your data, as they could potentially log, monitor, or even sell your browsing activity.
3. Data Breaches: If the VPN provider experiences a data breach, your personal information, including connection logs, could be exposed.
4. Jurisdiction Concerns: The provider may be located in a country with laws that could compel them to hand over user data to government agencies.
5. Third-party VPNs often assign the same IP address to multiple users, which can lead to security and privacy issues if someone else using the same IP engages in malicious activities. By running your own OpenVPN server, you eliminate this shared risk and have greater control over your network environment.


## Prerequisites
Before starting, ensure you have the following:

1. An AWS account with appropriate access to create and manage EC2 instances.
2. Basic knowledge of SSH and VPN concepts.
3. An OpenVPN-compatible device (Windows, macOS, Linux, iOS, or Android) for testing the VPN connection.

## Why AWS?
1. Scalability and Flexibility: AWS provides a highly scalable environment, allowing you to adjust resources based on your needs. Whether you need more capacity or additional features, AWS can accommodate your requirements with minimal hassle.
2. Cost-Effectiveness: AWS offers a pay-as-you-go pricing model, which can be more cost-effective compared to maintaining physical hardware. The Free Tier option further reduces initial costs for personal use.
3. Security: AWS includes robust security measures, such as VPCs, security groups, and IAM roles, which help in managing and securing your VPN environment.

## Why OpenVPN?
1. Open Source and Customizable: OpenVPN is open-source, meaning it's freely available and can be customized to meet specific needs. This provides flexibility and transparency that is not always present with commercial VPN services.
2. High Security: OpenVPN uses strong encryption protocols to secure data transmission. It offers robust security features, such as multi-factor authentication and detailed logging, to ensure your data remains private.
3. Wide Compatibility: OpenVPN is compatible with various operating systems and devices, making it easy to connect different types of client devices to the VPN.

## Setup instructions

Start by logging into your AWS Management Console. AWS provides a user-friendly web interface that allows you to manage your cloud resources. If you don’t already have an AWS account, you’ll need to create one. Once logged in, you’ll be able to access various AWS services.

Go to EC2: EC2 (Elastic Compute Cloud) is a service that allows you to run virtual servers (instances) in the cloud. From the AWS Management Console, locate and click on the "EC2" service under the "Compute" category.

Launch an EC2 Instance: In the EC2 dashboard, click on the “Launch Instance” button. This begins the process of creating a new virtual server. An instance is essentially a virtual machine that you can configure and control, and it will run your OpenVPN server.

Choose AMI: An AMI is a template that contains the software configuration (operating system, application server, and applications) required to launch your instance. AWS provides several pre-configured AMIs, or you can create your own.

Select OpenVPN Access Server from AWS Marketplace: AWS Marketplace offers a wide range of AMIs, including OpenVPN Access Server. Search for “OpenVPN Access Server” in the Marketplace. This AMI comes pre-configured with OpenVPN, which simplifies the setup process.

![image](https://github.com/user-attachments/assets/4d99aea0-b478-4567-884c-41c54be3f4e2)

Instance Type: AWS offers various instance types, each with different combinations of CPU, memory, storage, and networking capacity. Choose an instance type that meets your needs.

Free Tier Eligibility: If you’re using this VPN for personal use, you can opt for a free-tier eligible instance type like t2.micro. This instance type provides enough resources to run OpenVPN for a small number of users and is cost-effective as it falls under AWS’s Free Tier for the first year.

![image](https://github.com/user-attachments/assets/921f2d84-49f9-4cde-844d-f68c1a5a5acc)

Create a Key-pair.
Key Pair Creation: A key pair is used for secure SSH access to your EC2 instance. When you create a key pair, AWS will download a .pem file to your computer. This file contains your private key, which you’ll use to log in to your EC2 instance securely.

Download Key Pair: Store the .pem file securely, as it’s required for SSH access. If you lose this file, you won’t be able to connect to your instance.

When you create a key-pair, it will download the key.pem file. 
![image](https://github.com/user-attachments/assets/edd629f2-5ffd-4bd0-83fd-fd985d3cf454)

Launch your instance.
Launch the Instance: After selecting your instance type and configuring other settings like security groups (firewall rules), click “Launch Instance.” This will create and start your EC2 instance.

Access the Instance: Once the instance is running, click on the instance ID to view its details. AWS will provide instructions on how to connect to the instance using SSH.

![image](https://github.com/user-attachments/assets/60ccaca0-2bc1-4c92-af2d-ab435bb18848)


After you click connect, go to the instance to view how you can connect it using SSH client.

![image](https://github.com/user-attachments/assets/0c5475a0-9c12-4495-8e45-cd2674a6b8c8)

Copy the ssh command in example, and go to windows powershell or any SSH client like Putty to connect to your instance and configure the openVPN Access server.

SSH Access: To manage your instance, you need to connect to it using SSH (Secure Shell). AWS provides a command that you can use in a terminal or an SSH client like PuTTY on Windows. Copy the provided SSH command, which will look something like this
ssh -i "your-key.pem" openvpnas@your-instance-public-ip
Replace your-key.pem with the path to your downloaded key file and your-instance-public-ip with the public IP of your EC2 instance.


![image](https://github.com/user-attachments/assets/49eea39b-f10b-4d9a-9b66-61bd8eed55ee)

Login Issues: If you encounter login issues, ensure that you’re using openvpnas@your-instance-public-ip instead of root@your-instance-public-ip, as OpenVPN instances are configured to accept SSH connections under the openvpnas user.
![image](https://github.com/user-attachments/assets/24ab41b4-43dc-49cf-a119-d094dff9bdbd)

Accept License Agreement: Upon first login, you’ll be prompted to accept the OpenVPN license agreement. Type yes to agree and proceed with the setup.

Default Configuration: OpenVPN will prompt you with several configuration options. For most personal use cases, the default options are sufficient. Simply press Enter to accept the defaults.

![image](https://github.com/user-attachments/assets/cabba5ab-b8c6-4a0b-812d-c17a4c3b3cd0)

Set Admin Password: You’ll be asked to create a password for the OpenVPN admin account. This password is critical, as it will be used to access the OpenVPN Admin UI.

![image](https://github.com/user-attachments/assets/07a4529d-c7aa-4b56-94b8-dc431a8d1021)
![image](https://github.com/user-attachments/assets/679cce59-d6f9-4a02-91c6-19afeb5d0ac6)

Open Admin UI in browser using the link provided. 
Login to account using the default username: openvpn and password which you set while configuring OpenVPN access server.
After successfully logging, go to Configuration -> VPN Settings.
Go to Routing -> Select ‘yes, using NAT’ to provide access to VPN clients to private subnets. 

![image](https://github.com/user-attachments/assets/747fcbac-787d-4d23-a85f-11822946295d)


Click on save setting on the bottom of the page and click on ‘Update running server’ after setting have been applied. 
Now, this was ADMIN portal. Now, go to the user portal (https://3.16.37.111:943/) and login using same credentials. 
Now, you get the option to download the VPN client on whatever device you have – for windows/mac/ios/android.

![image](https://github.com/user-attachments/assets/760f564f-a1b4-41d6-8fa7-c9f24c616e25)

Once downloaded, install it.

![image](https://github.com/user-attachments/assets/2e11ff93-ed54-4841-987a-0754e538bd66)

Now, Just connect!

![image](https://github.com/user-attachments/assets/9a2f4d60-485f-424b-a785-8107cee4c9a5)
![image](https://github.com/user-attachments/assets/c29db261-42a5-4a8b-a45d-8bbdd3467a1f)

To verify, you can go to google and type 'What is my ip?' and it will show you your oublic IP address.
![image](https://github.com/user-attachments/assets/c7072a23-6581-4664-b874-42e1898d4b52)


After connecting to OpenVPN, you can check your IP again and it should not display your real Public IP address and instead show a VPN address hiding your real IP address. 
![image](https://github.com/user-attachments/assets/f192bc8c-b786-4c68-b8b8-a98b88595836)



