<p id="start" align="center">
<br>
<a href="#start"><img src="./assets/banner.png"></a>
<h1></h1>
</p>

![Wordpress](https://img.shields.io/badge/-WordPress-21759B?logo=wordpress&logoColor=white)
![AWS](https://img.shields.io/badge/-Amazon%20AWS-FF9900?logo=amazon-aws&logoColor=white)
[![Stars](https://img.shields.io/github/stars/holdennguyen/wordpress-route53-lightsail?style=social)](https://github.com/holdennguyen/wordpress-route53-lightsail/stargazers)

<br>
<p align="center">
<a href="#hosting-wordpress-in-the-amazon-lightsail">Hosting Wordpress in the Amazon Lightsail</a> | <a href="#config-static-ip">Config static IP</a> | <a href="#register-domain-in-amazon-route-53">Register Domain in Amazon Route 53</a> | <a href="#mapping-domain-to-ip-address">Mapping domain to IP address</a> | <a href="#setup-free-ssl-certificates-(https)">Setup free SSL Certificates (HTTPS)</a> | <a href="#login-to-wordpress-page">Login to WordPress page</a>
</p>

<h2>Hosting Wordpress in the Amazon Lightsail</h2>
Navigate to the <b>Lightsail</b> console from <a href="https://console.aws.amazon.com/" target="_blank">AWS Management Console</a>.<br>
    <picture><img width="500rem" src="./assets/aws-management-console.png"></picture><br><br>   
Select <b>Create instance</b>.<br>
    <picture><img width="500rem" src="./assets/create-instance.png"></picture><br><br>  
Select <b>Change AWS Region and Availability Zone</b> to choose the most suitable for your location.<br>
    <picture><img width="400rem" src="./assets/instance-location.png"></picture><br><br>
Region <b>Singapore</b> is fastest location for Vietnam. You can choose any Availability Zone.<br>
    <picture><img width="400rem" src="./assets/select-location.png"></picture><br><br>   
Select platform <b>Linux/Unix</b> and blueprint <b>WordPress (Apps + OS)</b>.<br>
    <picture><img width="400rem" src="./assets/instance-image.png"></picture><br><br>    
Select <b>Price Plan</b> base on your need.<br>
    <picture><img width="400rem" src="./assets/instance-plan.png"></picture><br><br>    
Before creating the instane, give the instance a name to identify it. Then select <b>Create instance</b>.<br>
    <picture><img width="500rem" src="./assets/confirm-create.png"></picture><br><br>  
<br>

<h2>Config Static IP</h2>
We need to wait for instance complete startup.<br>
    <picture><img width="300rem" src="./assets/instance-pending.png"></picture><br>
After 3-5 minutes, this instance will be running.<br>
    <picture><img width="300rem" src="./assets/instance-running.png"></picture><br>
Open instance <b>Connect tab</b> by click to its name, you can see the IP of my instance (IPv4): <b>13.212.150.202</b>.<br>
    <picture><img width="400rem" src="./assets/instance-connect.png"></picture><br>
This IP could be change if we restart or shutdown the instance that why we need to assign a static IP for <b>Amazon Route 53</b> service. Select <b>Networking</b> tab.<br>
    <picture><img width="400rem" src="./assets/instance-networking.png"></picture><br>
Click <b>Attach static IP</b> under PUBLIC IP.<br>
    <picture><img width="300rem" src="./assets/static-ip.png"></picture><br>
Give the IP a name to identify, then select <b>Create and attach</b>.<br>
    <picture><img width="300rem" src="./assets/static-ip-complete.png"></picture><br>
Now my instance has a <b>new IP (static): 13.229.25.92</b> attach to it. Save this IP for step mapping domain in the next step.<br>
    <picture><img width="400rem" src="./assets/new-static-ip.png"></picture><br>

<h2>Register Domain in Amazon Route 53</h2>
Navigate to the <b>Route 53</b> console from <a href="https://console.aws.amazon.com/" target="_blank">AWS Management Console</a>.<br>
    <picture><img width="500rem" src="./assets/route53.png"></picture><br><br>
Select <b>Registered domains</b> in the left side pannel.<br>
    <picture><img width="500rem" src="./assets/route53-console.png"></picture><br><br>
Choose <b>Register Domain</b> button to register new domain by Amazon Route 53. You can also choose <b>Transfer Domain</b> to use your domain that you already have in other registrars (NameCheap, Google Domain, GoDaddy, Bluehost...)<br>
    <picture><img width="300rem" src="./assets/register-domain.png"></picture><br><br>
Pick the domain, then <b>Add to cart</b>. Select duration (year) in the right side <b>Shopping cart</b>, click <b>Continue</b> to process next step.<br>
    <picture><img width="200rem" src="./assets/shopping-cart.png"></picture><br><br>
After complete fill in <b>Contact Details</b> and step <b>Verify & Purchase</b><br><br>
    <picture><img width="500rem" src="./assets/domain-complete.png"></picture><br><br>
AWS will send you an email to get your confirmation.<br>
    <picture><img width="500rem" src="./assets/domain-verify.png"></picture><br><br>

<h2>Mapping domain to IP address</h2>
In the <b>Route 53</b> console, select <b>Hosted zones</b> in the left side pannel.<br>
    <picture><img width="500rem" src="./assets/route53-hosted-zones.png"></picture><br><br>
When your domain was registered sucessfully, you will see its hosted zone of this domain. Click to this name<br>
    <picture><img width="400rem" src="./assets/hosted-zones-name.png"></picture><br><br>
Click <b>Create record</b><br>
    <picture><img width="400rem" src="./assets/click-create-record.png"></picture><br><br>
Leave <b>Record name</b> box empty, <b>Record type</b> select <b>A - Routes traffic to an IPv4 address and some AWS resources</b>. Paste the static IPv4 from step <b>Config Static IP</b> <a target="_blank">13.229.25.92</a> to <b>Value</b> box.<br>
    <picture><img width="400rem" src="./assets/create-record.png"></picture><br><br>
Click <b>Add another record</b>, then fill in same as the previous record but type <b>www</b> in the <b>Record name</b> box. Then choose <b>Create records</b> button in the bottom.<br>
    <picture><img width="400rem" src="./assets/create-another-record.png"></picture><br><br>
For more information, see <a href="https://aws.amazon.com/getting-started/hands-on/map-your-domain-at-route53-to-lightsail/3/">Map your domain at Amazon Route 53 to your Lightsail resources</a>.

<h2>Setup free SSL Certificates (HTTPS)</h2>
Open the <b>Lightsail</b> console, click the <b>terminal button</b> (in the right of instance name) in your <b>WordPress instance</b><br>
    <picture><img width="300rem" src="./assets/instance-running.png"></picture><br><br>
to open the <b>terminal window</b>.<br>
    <picture><img width="400rem" src="./assets/wordpress-terminal.png"></picture><br><br>
In the terminal, run this command: <code>sudo /opt/bitnami/bncert-tool</code><br>
Type your domain to <b>Domain list [ ]:</b> then input <b>y</b> (because we also create record for subdomain <b>www</b> in the previous step).<br>
Continue input <b>y</b> for next question <b>Enable HTTP to HTTPS redirection [Y/n]:</b><br>
In the next two question <b>from www</b> and <b>to www</b>, just input <b>y</b> for one.<br>
Input <b>y</b> for the rest and then we done.<br>
For more information, see <a href="https://aws.amazon.com/premiumsupport/knowledge-center/linux-lightsail-ssl-bitnami/">Install SSL certificates on Bitnami stacks for Lightsail</a>.

<h2>Login to WordPress page</h2>
Open the <b>terminal window</b> of <b>WordPress instance</b>.<br>
    <picture><img width="400rem" src="./assets/wordpress-terminal.png"></picture><br><br>
Run this command to get the password:<code>cat $HOME/bitnami_application_password</code><br>
Your username is <b>user</b>. 
<br>
For more information, see <a href="https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-quick-start-guide-wordpress" target="_blank">Quick start guide: WordPress on Amazon Lightsail</a>.

<p align="right"><a href="#start"><img width="45rem" src="./assets/top.png"></a></p>
