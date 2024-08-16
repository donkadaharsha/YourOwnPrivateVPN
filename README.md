# YourOwnPrivateVPN
A secure, custom VPN setup on AWS using OpenVPN Server, providing private network access and enhanced privacy.

## Project Overview
This project demonstrates the creation of a private VPN using AWS and OpenVPN Server. By leveraging the flexibility and scalability of AWS, I configured a secure and customizable VPN environment that ensures enhanced privacy and control over network traffic. This setup allows for secure remote access to resources, bypassing geo-restrictions, and protecting online activities from third-party monitoring. The project includes detailed instructions on deploying the OpenVPN server on an EC2 instance, configuring security groups, and connecting client devices to the VPN.

## Prerequisites
Before starting, ensure you have the following:

An AWS account with appropriate access to create and manage EC2 instances.
Basic knowledge of SSH and VPN concepts.
An OpenVPN-compatible device (Windows, macOS, Linux, iOS, or Android) for testing the VPN connection.

## Setup instructions

Login to aws amazon console.
Go to EC2 -> Launch an EC2 instance.
Choose AMI -> Go to AWS MarketPlace and select OpenVPN access server.

![image](https://github.com/user-attachments/assets/4d99aea0-b478-4567-884c-41c54be3f4e2)

If you are using it for personal use, Select 'free tier' eligible instance type (t2.micro) to save cost.
![image](https://github.com/user-attachments/assets/921f2d84-49f9-4cde-844d-f68c1a5a5acc)

Create a Key-pair.

When you create a key-pair, it will download the key.pem file. 
![image](https://github.com/user-attachments/assets/edd629f2-5ffd-4bd0-83fd-fd985d3cf454)

Launch your instance and click on the instance you created. Click connect. 
![image](https://github.com/user-attachments/assets/60ccaca0-2bc1-4c92-af2d-ab435bb18848)


After you click connect, go to the instance to view how you can connect it using SSH client.

![image](https://github.com/user-attachments/assets/0c5475a0-9c12-4495-8e45-cd2674a6b8c8)

Copy the ssh command in example, and go to windows powershell or any SSH client like Putty to connect to your instance and configure the openVPN Access server.

![image](https://github.com/user-attachments/assets/49eea39b-f10b-4d9a-9b66-61bd8eed55ee)
You might get the above error, so you need to login as openvpnas@ipaddr instead of root@ipaddr.
![image](https://github.com/user-attachments/assets/24ab41b4-43dc-49cf-a119-d094dff9bdbd)

Click 'yes' to agreement.
![image](https://github.com/user-attachments/assets/cabba5ab-b8c6-4a0b-812d-c17a4c3b3cd0)

All other following questions, you can choose default(enter yes).

Create a password to login to your openVPN access server.
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
![image](https://github.com/user-attachments/assets/a4bc0088-03c6-4fb0-9917-dee8bfd2aa5e)

After connecting to OpenVPN, you can check your IP again and it should not display your real Public IP address and instead show a VPN address hiding your real IP address. 
![image](https://github.com/user-attachments/assets/f192bc8c-b786-4c68-b8b8-a98b88595836)



