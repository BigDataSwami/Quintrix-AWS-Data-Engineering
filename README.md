#1. AWS Basics - Install WP in 
This tutorial is free tier eligible. 


#2. Create a WordPress instance in Lightsail
Complete the following steps to get your WordPress instance up and running on Lightsail.

Note: For more information about creating an instance in Lightsail, see Creating an Amazon Lightsail instance in the Lightsail documentation.
a. Sign into the Lightsail console. 

b. On the Instances tab of the Lightsail home page, choose Create instance.
amazon-wordpress-tutorial-01
c. Choose the AWS Region and Availability Zone for your instance.
amazon-wordpress-tutorial-02
d. Choose your instance image.
 
Choose Linux/Unix as the platform.
Choose WordPress as the blueprint.
amazon-wordpress-tutorial-03
e. Choose an instance plan.
 
A plan includes a low, predictable cost, machine configuration (RAM, SSD, vCPU), and data transfer allowance. You can try the $3.50 USD Lightsail plan without charge for one month (up to 750 hours). AWS credits one free month to your account.
mike3
f. Enter a name for your instance. 
 
Resource name guidelines:
Must be unique within each AWS Region in your Lightsail account.
Must contain 2 to 255 characters.
Must start and end with an alphanumeric character or number.
Can include alphanumeric characters, numbers, periods, dashes, and underscores.
amazon-wordpress-tutorial-04
g. Choose Create instance.  
3. Connect to your instance via SSH and get the password for your WordPress website
The default password to sign in to the administration dashboard of your WordPress website is stored on the instance.

Complete the following steps to connect to your instance using the browser-based SSH client in the Lightsail console, and get the password for the administration dashboard.

Note: For more information, see Getting the application user name and password for your Certified by Bitnami' instance in Amazon Lightsail.

a. On the Instances tab of the Lightsail home page, choose the SSH quick-connect icon for your WordPress instance.
amazon-wordpress-tutorial-05
b. After the browser-based SSH client window opens, enter the following command to retrieve the default application password:
cat $HOME/bitnami_application_password
c. Make note of the password displayed on the screen. You use it later to sign in to the administration dashboard of your WordPress website.
amazon-wordpress-tutorial-06
4. Sign in to the administration dashboard of your WordPress website
Now that you have the password for the administration dashboard of your WordPress website, you can sign in. In the administration dashboard, you can change your user password, install plugins, change the theme of your website, and more.

Complete the following steps to sign in to the administration dashboard of your WordPress website.

Note: For more information, see Getting the application user name and password for your Certified by Bitnami' instance in Amazon Lightsail.

a. In a browser, go to:

http://PublicIpAddress/wp-login.php
In the address, replace PublicIpAddress with the public IP address of your WordPress instance. You can get your instance's public IP address from the Lightsail console as shown in the following image:
wordpress real 
b. Log into your instance. 

In the Username or Email Address box, enter "user".
Password box, enter the default password obtained earlier in this tutorial.
Choose Log in. 
amazon-wordpress-tutorial-07
You are now signed in to the administration dashboard of your WordPress website where you can perform administrative actions. For more information about administering your WordPress website, see the WordPress Codex in the WordPress documentation.

amazon-wordpress-tutorial-08
5. Create a Lightsail static IP address and attach it to your WordPress instance
The default public IP for your WordPress instance changes if you stop and start your instance. A static IP address, attached to an instance, stays the same even if you stop and start your instance.

Complete the following steps to create a static IP address and attach it to your WordPress instance.

Note: For more information, see Create a static IP and attach it to an instance in Amazon Lightsail.
a. On the Instances tab of the Lightsail home page, choose your running WordPress instance.
amazon-wordpress-tutorial-05
b. Choose the Networking tab, then choose Create static IP.

amazon-wordpress-tutorial-10
c. The static IP location, and attached instance are pre-selected based on the instance that you chose earlier in this tutorial.

 
amazon-wordpress-tutorial-11
d. Name your static IP, then choose Create. 

amazon-wordpress-tutorial-12
6. Create a Lightsail DNS zone and map a domain to your WordPress instance
Transfer management of your domain's DNS records to Lightsail. This allows you to more easily map a domain to your WordPress instance, and manage more of your website’s resources using the Lightsail console.

Complete the following steps to create a Lightsail DNS zone and map a domain to your WordPress instance.

Note: For more information, see Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail.

a. On the Networking tab of the Lightsail home page, choose Create DNS zone. 

amazon-wordpress-tutorial-13
b. Enter your domain, then choose Create DNS zone. 

amazon-wordpress-tutorial-14
c. Make note of the name server address listed on the page. 

You add these name server addresses to your domain name’s registrar to transfer management of your domain’s DNS records to Lightsail.

amazon-wordpress-tutorial-15
d. After management of your domain’s DNS records are transferred to Lightsail, add an A record to point the apex of your domain to your WordPress instance, as follows:
 
You add these name server addresses to your domain name’s registrar to transfer management of your domain’s DNS records to Lightsail.
 
1. In the DNS zone for your domain, choose Add record.
 
2. In the Subdomain box, enter an @ symbol to map the apex of your domain (such    as example.com) to your instance. The @ symbol explicitly symbolizes that you’re adding an apex record. It is not added as a subdomain.
 
3. In the Maps to box, choose the static IP that you attached to the WordPress instance in the previous step of this tutorial.
 
4. Choose the save icon.
 
Allow time for the change to propagate through the internet's DNS before your domain begins routing traffic to your WordPress instance.
amazon-wordpress-tutorial-16
