# Network-Security
## Description
This challenge requires knowledge of:
* Drop Zones
* Firewalls Configuration
## Environments Used
* Ubuntu
## Drop Zone Lab
1. Ensure UFW  is not running.
> $sudo apt remove ufw
> 
> ![UFW](https://github.com/DaisyDurand/Network-Security/assets/147094227/15229a61-517a-4661-a4c2-a19356141c97)
2. Enable and start firewalld
> $sudo /etc/init.d/firewalld start  
> $sudo systemcl enable firewalld
> 
> ![Enable and Start Firewalld](https://github.com/DaisyDurand/Network-Security/assets/147094227/2db3dd60-bbec-48b4-8852-a56e0d359386)
3. Confirm the service is running
