# Network-Security
## Description
This challenge requires knowledge of:
* Security zones
* Firewall Configuration
## Environments Used
* Ubuntu
## Drop Zone Lab
1. Uninstall UFW
> $sudo apt remove ufw
> 
> ![UFW](https://github.com/DaisyDurand/Network-Security/assets/147094227/15229a61-517a-4661-a4c2-a19356141c97)
2. Enable and start firewalld
> $sudo /etc/init.d/firewalld start  
> $sudo systemcl enable firewalld
> 
> ![Enable and Start Firewalld](https://github.com/DaisyDurand/Network-Security/assets/147094227/2db3dd60-bbec-48b4-8852-a56e0d359386)
3. Confirm the service is running
> $service firewalld status
> 
> ![Confirm Firewalld is running](https://github.com/DaisyDurand/Network-Security/assets/147094227/6e438ffe-06da-4aa5-b195-df18b81a2ff4)
4. List all firewall rules currently configured
> $sudo firewall-cmd --list-all
>
> ![List all configured firewall rules ](https://github.com/DaisyDurand/Network-Security/assets/147094227/6082dfac-ad44-46da-8cf8-1a7da317c042)
5. List all supported service types that can be enabled
> $sudo firewall-cmd --get-services
> 
> ![List all supported service types](https://github.com/DaisyDurand/Network-Security/assets/147094227/d5233c63-510e-4d40-860f-88fc72c1a1e7)
6. Zone views
> $sudo firewall-cmd --list-all-zones
>
> The zones in the images below were previously configured.
> 
> ![Zone views](https://github.com/DaisyDurand/Network-Security/assets/147094227/28455b81-1789-4e22-97f9-2ae74349a702)
>
> ![zone views 2](https://github.com/DaisyDurand/Network-Security/assets/147094227/a59207da-1978-4282-a2a0-2c1d871fbcd0)
>
> ![zone views 3](https://github.com/DaisyDurand/Network-Security/assets/147094227/30d43894-1eff-4c7d-9a89-a8c7d3e670a2)
>
> ![zone views 4](https://github.com/DaisyDurand/Network-Security/assets/147094227/afc3e9da-d440-4e0b-8c05-4a14034389a3)
>
> ![zone views 5](https://github.com/DaisyDurand/Network-Security/assets/147094227/7ccbd734-2fc0-4b73-aefa-582bde7951ab)
7. Create zones for web, sales and mail
> $sudo firewall-cmd --permanent --new-zone=web
>
> $sudo firewall-cmd --permanent --new-zone=sales
>
> $sudo firewall-cmd --permanent --new-zone=mail
>
> ![Create zones](https://github.com/DaisyDurand/Network-Security/assets/147094227/27694849-d89d-4e57-8b1b-485b6f1bb583)
8. Set the zones to their designated interfaces
> $sudo firewall-cmd --permanent --zone=public --add-interface=eth0
>
> ![set the zones](https://github.com/DaisyDurand/Network-Security/assets/147094227/93919bd5-959e-493b-8f6e-c6218fba18a5)
> 
> $sudo firewall-cmd --permanent --zone=web --add-interface=eth1
> 
>![Set the zone web](https://github.com/DaisyDurand/Network-Security/assets/147094227/48b0dfd9-f0e2-4964-a5f4-9600a3917b27)
> 
> $sudo firewall-cmd --permanent --zone=sales --add-interface=eth2
> ![set the zones sales](https://github.com/DaisyDurand/Network-Security/assets/147094227/68a5c358-1404-4dcd-8d4d-9989896ec675)
> 
> $sudo firewall-cmd --permanent --zone=mail --add-interface=eth3
> ![set the zones web and mail](https://github.com/DaisyDurand/Network-Security/assets/147094227/fe4f4d11-8888-49eb-b30a-3b04dc0dded6)
>
9. Add services to the active zones  
> Public zone
>
> $sudo firewall-cmd --permanent --zone=public --add-service=HTTP
>
> ![add service to public HTTP](https://github.com/DaisyDurand/Network-Security/assets/147094227/36bcd480-cb65-4e4e-b4fb-1953f3892f75)
> 
> $sudo firewall-cmd --permanent --zone=public --add-service=HTTPS
>
> ![add service to public HTTPS](https://github.com/DaisyDurand/Network-Security/assets/147094227/25d63057-b6c4-43c8-8e9d-865db9806cba)
> 
> $sudo firewall-cmd --permanent --zone=public --add-service=POP3
>
> ![add service tp public POP3](https://github.com/DaisyDurand/Network-Security/assets/147094227/42035cb2-ee4e-471c-b763-7b0e44e52a54)
> 
> $sudo firewall-cmd --permanent --zone=public --add-service=SMTP
>
> ![add service to publid SMTP](https://github.com/DaisyDurand/Network-Security/assets/147094227/beac4f81-ece5-4795-b2fa-711f4124afe3)
>
> Web zone
>
> $sudo firewall-cmd --permanent --zone=web --add-service=HTTP
> 
> ![add service to web HTTP](https://github.com/DaisyDurand/Network-Security/assets/147094227/aa7f250f-d026-49db-a1b6-85229b719bfd)
>
> Sales zone
> 
> $sudo firewall-cmd --permanent --zone=sales --add-service=HTTPS
>
> ![add service to sales HTTPS](https://github.com/DaisyDurand/Network-Security/assets/147094227/989bf080-7557-4d5e-8faa-0bcb77f5bb99)
>
> Mail zone
>
> $sudo firewall-cmd --permanent --zone=mail --add-service=SMTP
> $sudo firewall-cmd --permanent --zone=mail --add-service=POP3
>
> ![add service to mail SMTP and POP3](https://github.com/DaisyDurand/Network-Security/assets/147094227/d36e23e3-0c89-4e1d-8e35-84a8e219343f)

10. Add adversaries to the drop zone
>
> $sudo firewall-cmd --permanent --zone=drop --add-rich-rule=”rule family=’ipv4’ source address=’10.208.56.23’ reject”
>
>![Drop rule 1](https://github.com/DaisyDurand/Network-Security/assets/147094227/dc77c50c-fd57-4411-9ccc-1ffd16d9bcb2)
>
> $sudo firewall-cmd --permanent --zone=drop --add-rich-rule=”rule family=’ipv4’ source address=’135.95.103.76’ reject”
>
>![Drop rule 2](https://github.com/DaisyDurand/Network-Security/assets/147094227/0defe234-eec2-4e6c-934e-3e0b6254279a)
>
> $sudo firewall-cmd --permanent --zone=drop --add-rich-rule=”rule family=’ipv4’ source address=’76.34.169.118’ reject”
>
>![Drop rule 3](https://github.com/DaisyDurand/Network-Security/assets/147094227/3e903afb-eddf-4bef-b097-aa85fcb00230)

11. Make rules permanent, then reload them
>
> $sudo firewall-cmd --reload
>
>![Make rules permanent](https://github.com/DaisyDurand/Network-Security/assets/147094227/7f4ebba8-ef77-4ea0-bd44-c435eb92fa78)

12. View active zones
>
> $sudo firewall-cmd --get-zones
>
>![View active zones](https://github.com/DaisyDurand/Network-Security/assets/147094227/86362dd5-e3f5-4dfb-a2c2-2670b69eecca)

13. Block an IP address
>
> $sudo firewall-cmd --permanent --zone=public --add-rich-rule=”rule family=’ipv4’ source address=’138.138.0.3’ reject”
>
>![Block an IP address](https://github.com/DaisyDurand/Network-Security/assets/147094227/292d70bd-5ea4-4a84-8b06-7cda66da210c)

14. Block ping/ICMP requests
>
> $sudo firewall-cmd --permanent --zone=public --add-icmp-block=echo-request
>
>![Block ping](https://github.com/DaisyDurand/Network-Security/assets/147094227/230a4c7d-9612-4bf5-9a3c-46bff4127c8f)

15. Rule check
>
> $sudo firewall-cmd --zone=web --list-all
>
>![List web](https://github.com/DaisyDurand/Network-Security/assets/147094227/e486c721-78ac-4c93-8938-36b2586a68e5)
>
>  $sudo firewall-cmd --zone=mail --list-all
>
>![List mail](https://github.com/DaisyDurand/Network-Security/assets/147094227/ad13a005-0683-40a7-809a-dc03eb3286a4)
>
> $sudo firewall-cmd --zone=sales --list-all
>
>![List sales](https://github.com/DaisyDurand/Network-Security/assets/147094227/40348c2c-093d-44d3-bee6-402fc45bb313)
>
> $sudo firewall-cmd --zone=drop --list-all
>
>![List drop](https://github.com/DaisyDurand/Network-Security/assets/147094227/7ab3e84f-5445-42af-8cec-57134b045e91)
>
> $sudo firewall-cmd --zone=public --list-all
>
>![List public](https://github.com/DaisyDurand/Network-Security/assets/147094227/9089c362-2644-40c7-b8d8-de447fcad10d)
