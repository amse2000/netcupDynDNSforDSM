# ownDynDNS
DNS-API netcup-hosted dynamic DNS php script for FRITZ!Box and Synology DSM 

## Authors (Thank you!)
* Felix Kretschmer [@fernwerker](https://github.com/fernwerker)
* Philipp Tempel [@philipptempel](https://github.com/philipptempel)
* Branko Wilhelm [@b2un0](https://github.com/b2un0)

## Usage
### Installation
* Copy all files to your webspace
* create a copy of `.env.dist` as `.env` and configure:
  * `username` -> The username for your Router to authenticate (so not everyone can update your DNS)
  * `password` -> password for your Router
  * `apiKey` -> API key which is generated in netcup CCP
  * `apiPassword` -> API password which is generated in netcup CCP
  * `customerId` -> your netcup Customer ID
  * `debug` -> true|false enables debug mode and generates output of update.php (normal operation has no output)
  
* Create each host record in your netcup CCP (DNS settings) before using the script. The script does not create any missing records.

### AVM FRITZ!Box Settings
* Go to "Internet" -> "Freigaben" -> "DynDNS"
* Choose "Benutzerdefiniert"
* Update-URL: `https://<url of your webspace>/update.php?user=<username>&password=<pass>&ipv4=<ipaddr>&ipv6=<ip6addr>&domain=<domain>`
  * only the url needs to be adjusted, the rest is automatically filled by your AVM FRITZ!Box
  * http or https is possible if valid SSL certificate (e.g. Let's Encrypt)
* Single Domain:
  * Domainname: `<host record that is supposed to be updated>`
* Multiple Domains:
  * Domainname: `<first host record that is supposed to be updated>,<second host record that is supposed to be updated>,....`
* Username: `<username as defined in .env file>`
* Password: `<password as definied in .env file>`


### DSM-Settings
* Go to "Systemsteuerung" -> "Externer Zugriff" -> "DDNS" -> "Anpassen"
* Choose Name for "Serviceanbieter" for example "Netcup"
* Update-URL: `https://<url of your webspace>/update.php?user=__USERNAME__&password=__PASSWORD__&ipv4=__MYIP__&domain=__HOSTNAME__`
  * only the url needs to be adjusted, the rest is automatically filled by your Diskstation DSM
  * http or https is possible if valid SSL certificate (e.g. Let's Encrypt)
* Single Domain:
  * Hostname: `<host record that is supposed to be updated>`
* Multiple Domains:
  * Hostname: `<first host record that is supposed to be updated>,<second host record that is supposed to be updated>,....`
* Benutzername/Email: `<username as defined in .env file>`
* Passwort/Schlüssel: `<password as definied in .env file>`


## References
* DNS API Documentation: https://ccp.netcup.net/run/webservice/servers/endpoint.php
* Source of dnsapi.php: https://ccp.netcup.net/run/webservice/servers/endpoint.php?PHPSOAPCLIENT

## License
Published under GNU General Public License v3.0  
&copy; Felix Kretschmer, 2021
