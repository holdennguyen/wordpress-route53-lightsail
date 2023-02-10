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
<a href="#hosting-wordpress-in-the-amazon-lightsail">Hosting Wordpress in the Amazon Lightsail</a> | <a href="#config-static-ip">Config static IP</a> | <a href="#usage-examples">Usage Examples</a> | <a href="#how-does-it-work">How does it work?</a> | <a href="#features">Features</a> | <a href="#appendix-boptional-request--response-headers">Optional Headers</a> | <a href="#appendix-acommand-line-options">CLI</a> | <a href="Cheatsheet.md">Cheatsheet</a>
</p>

<h2>Hosting Wordpress in the Amazon Lightsail</h2>

<ol>
    <li>Navigate to the <b>Lightsail</b> console from <a href="https://console.aws.amazon.com/" target="_blank">AWS Management Console</a>.<br><br>
    <a href=""><img src="./assets/aws-management-console.png"></a><br><br><br>
    </li>
    <li>Select <b>Create instance</b>.<br><br>
    <a href=""><img src="./assets/create-instance.png"></a><br><br><br>
    </li>
    <li>Select <b>Change AWS Region and Availability Zone</b> to choose the most suitable for your location.<br>
    <a href=""><img src="./assets/instance-location.png"></a><br><br>
    Region <b>Singapore</b> is fastest location for Vietnam. You can choose any Availability Zone.<br><br>
    <a href=""><img src="./assets/select-location.png"></a><br><br>
    </li>
    <li>Select platform <b>Linux/Unix</b> and blueprint <b>WordPress (Apps + OS)</b>.<br><br>
    <a href=""><img src="./assets/instance-image.png"></a><br><br><br>
    </li>
    <li>Select <b>Price Plan</b> base on your need.<br><br>
    <a href=""><img src="./assets/instance-plan.png"></a><br><br><br>
    </li>
    <li>Before creating the instane, give the instance a name to identify it. Then select <b>Create instance</b>.<br><br>
    <a href=""><img src="./assets/confirm-create.png"></a><br><br><br>
    </li>
</ol>
That's it!
<br><br>

<h2>Config Static IP</h2>

We need to wait for instance complete startup.
    <a><img src="./assets/instance-pending.png"></a><br>
After 3-5 minutes, this instance will be running.
    <a><img src="./assets/instance-running.png"></a><br>

<p align="right"><a href="#start"><img width="45rem" src="./assets/top.png"></a></p>