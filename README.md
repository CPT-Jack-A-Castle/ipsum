![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-04-16)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|10
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|10
162.247.74.27|turing.tor-exit.calyxinstitute.org|10
185.220.102.4|communityexit.torservers.net|10
171.25.193.78|tor-exit4-readme.dfri.se|10
185.220.101.1|-|10
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|9
185.220.101.215|-|9
185.56.80.65|onion.xor.sc|9
178.165.72.177|178-165-72-177-kh.maxnet.ua|9
185.100.87.202|-|9
185.191.124.150|-|9
198.144.121.93|-|9
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|9
46.182.21.248|tor-exit-relay.anonymizing-proxy.digitalcourage.de|9
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|9
185.220.101.207|-|9
185.220.101.206|-|9
185.220.102.244|185-220-102-244.torservers.net|8
185.220.102.243|185-220-102-243.torservers.net|8
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|8
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|8
178.20.55.18|marcuse-2.nos-oignons.net|8
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|8
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|8
192.42.116.14|this-is-a-tor-exit-node-hviv114.hviv.nl|8
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|8
198.144.120.234|-|8
166.70.207.2|this.is.a.tor.node.xmission.com|8
185.220.101.211|-|8
185.220.101.212|-|8
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|8
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|8
103.151.145.10|tor-exit1.ny1.ap.foundation|8
209.127.17.234|-|8
81.161.63.103|-|8
45.153.160.138|-|8
89.234.157.254|marylou.nos-oignons.net|8
84.53.192.243|-|8
185.191.124.153|-|8
171.25.193.77|tor-exit1-readme.dfri.se|8
194.165.16.89|-|8
162.247.74.213|snowden.tor-exit.calyxinstitute.org|8
198.96.155.3|exit.tor.uwaterloo.ca|8
77.247.181.165|politkovskaja.torservers.net|8
161.97.77.212|vmi517316.contaboserver.net|8
185.220.103.5|chelseamanning.tor-exit.calyxinstitute.org|8
66.230.230.230|-|8
171.25.193.20|tor-exit0-readme.dfri.se|8
171.25.193.25|tor-exit5-readme.dfri.se|8
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|8
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|8
23.129.64.202|-|8
95.128.43.164|exit-1.fr.tor.aquaray.com|8
193.239.232.101|-|8
209.141.59.180|freedomisnotfree|8
185.220.101.204|-|8
185.220.101.201|-|8
104.244.79.172|tor1.prismless.org|7
209.141.54.71|-|7
191.5.55.11|11-55-5-191.viartelecom.com.br|7
185.220.102.245|185-220-102-245.torservers.net|7
185.220.102.240|185-220-102-240.torservers.net|7
185.220.102.241|185-220-102-241.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
195.254.135.76|-|7
185.107.70.202|tor-exit.r3.darknet.dev|7
111.229.4.66|-|7
164.52.24.164|-|7
23.129.64.237|-|7
23.129.64.236|-|7
23.129.64.234|-|7
23.129.64.230|-|7
185.107.47.171|tor-exit.r2.darknet.dev|7
23.129.64.209|-|7
45.133.1.18|-|7
94.142.241.194|tor-exit.vrij-heid.nl|7
23.129.64.208|-|7
23.129.64.203|-|7
209.127.17.242|-|7
185.220.100.252|tor-exit-1.zbau.f3netze.de|7
104.244.77.95|-|7
67.207.88.180|-|7
94.230.208.147|tor3e1.digitale-gesellschaft.ch|7
192.42.116.19|this-is-a-tor-exit-node-hviv119.hviv.nl|7
185.130.44.108|tor-exit-se1.privex.cc|7
185.220.101.218|-|7
185.220.101.216|-|7
185.220.101.213|-|7
140.143.241.67|-|7
205.185.126.173|-|7
121.4.105.116|-|7
138.68.9.15|-|7
116.110.68.228|-|7
162.247.74.216|phoolandevi.tor-exit.calyxinstitute.org|7
207.244.70.35|-|7
213.202.233.34|srv1033.dedicated.server-hosting.expert|7
167.86.94.107|master-of-disaster.tor-exit.laarnes.nl|7
185.233.100.23|elenagb.nos-oignons.net|7
185.67.82.114|tor-ou.effi.org|7
62.102.148.69|-|7
62.102.148.68|-|7
94.142.244.16|tor-exit.vrij-heid.nl|7
185.220.102.246|185-220-102-246.torservers.net|7
45.153.160.137|-|7
45.153.160.136|-|7
192.42.116.23|this-is-a-tor-exit-node-hviv123.hviv.nl|7
192.42.116.20|this-is-a-tor-exit-node-hviv120.hviv.nl|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
212.95.137.19|-|7
195.206.105.217|zrh-exit.privateinternetaccess.com|7
185.34.33.2|tor.laquadrature.net|7
162.247.74.202|djb.tor-exit.calyxinstitute.org|7
162.247.74.201|kunstler.tor-exit.calyxinstitute.org|7
162.247.74.200|kiriakou.tor-exit.calyxinstitute.org|7
162.247.74.204|billsf.tor-exit.calyxinstitute.org|7
45.125.65.45|-|7
109.104.151.112|-|7
82.221.131.5|-|7
41.226.25.4|-|7
185.191.124.151|-|7
23.129.64.235|-|7
23.129.64.231|-|7
185.220.101.9|-|7
185.220.101.3|-|7
209.141.48.202|-|7
18.27.197.252|wholesomeserver.media.mit.edu|7
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|7
185.247.224.14|tor-exit-ro.letztermensch.com|7
209.141.54.195|tor1.friendlyexitnode.com|7
185.170.114.25|this-is-a-tor-node---10.artikel5ev.de|7
185.130.44.124|tor.exit.node|7
185.165.168.229|-|7
209.141.52.57|mail.capellinimarketing.com|7
185.220.102.8|185-220-102-8.torservers.net|7
206.189.138.99|-|7
77.247.181.163|lumumba.torservers.net|7
182.254.130.92|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
185.213.155.169|-|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
109.104.151.108|-|7
217.170.206.138|tor-exit-6138.nortor.no|7
176.10.99.200|accessnow.org|7
198.144.120.177|-|7
158.69.35.227|tor-exit-ca.letztermensch.com|7
104.131.16.66|-|7
185.191.124.143|-|7
185.36.81.58|-|7
185.220.102.252|tor-exit-relay-6.anonymizing-proxy.digitalcourage.de|7
185.220.102.251|tor-exit-relay-5.anonymizing-proxy.digitalcourage.de|7
185.220.103.10|token-dispenser.netpimp.com|7
85.95.191.186|85-95-191-186.saransk.ru|7
64.113.32.29|tor.t-3.net|7
23.129.64.200|-|7
23.129.64.201|-|7
23.129.64.206|-|7
23.129.64.204|-|7
23.129.64.205|-|7
144.172.118.4|Houston.Texas4Tor.com|7
45.129.56.200|-|7
82.221.128.191|-|7
185.220.101.198|-|7
185.220.101.197|-|7
147.139.163.83|-|7
105.203.195.68|host-105.203.195.68.etisalat.com.eg|7
23.129.64.247|-|7
217.170.204.126|tor-exit-4126.nortor.no|7
209.141.48.144|tor.relay.com|7
162.247.73.192|mario-louis-sylvester-lap.tor-exit.calyxinstitute.org|7
198.98.51.189|tor.teitel.net|7
185.220.101.208|-|7
185.220.101.205|-|7
185.220.101.203|-|7
185.220.101.202|-|7
80.67.172.162|algrothendieck.nos-oignons.net|7
