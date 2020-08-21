# Home IP Plan

Home AS30746, transit provided by AS60036

* 44.131.4.0/24 Home AMPRnet prefix
* 193.47.147.0/24             Home PI prefix
  * **193.47.147.0/28**           Loopbacks and /32's
    * 193.47.147.1            rt1.home.nat.ms
    * 193.47.147.2            
    * 193.47.147.3            
    * 193.47.147.6            VIP Caddy  NAT'd
    * 193.47.147.7            VIP MQTT broker
    * 193.47.147.8            VIP DNS resolver 1   BGP 
    * 193.47.147.9            VIP DNS resolver 2   BGP
    * 193.47.147.10           VIP syslog
    * 193.47.147.11           VIP time NTP/SNTP
    * 193.47.147.12           NAT src guests
    * 193.47.147.13           NAT src VPN L2TP users
    * 193.47.147.14           NAT src home
    * 193.47.147.15           NAT src Wifi AP management
    * 193.47.147.16           NAT src IOT
    * 193.47.147.17           NAT src CCTV
    * 193.47.147.18
    * 193.47.147.19           NAT/VIP Unifi Controller
    
    * 193.47.147.20/30        
      * 193.47.147.21         
      * 193.47.147.22         
    * 193.47.147.24/30
      * 193.47.147.25         sw1
      * 193.47.147.26         host
    * 193.47.147.28/30
      * 193.47.147.29         sw1
      * 193.47.147.30         rt3
  * **193.47.147.32/28**          Linknets
    * 193.47.147.32/29
      * 193.47.147.33         rt1
      * 193.47.147.34         moby1
      * 193.47.147.35         moby2
      * 193.47.147.36         moby3
    * 193.47.147.40/29
      * 193.47.147.41         rt1
      * 193.47.147.42         pve1
      * 193.47.147.43         pve1-ipmi
  * **193.47.147.56/29**          Pole
    * 193.47.147.57           sw1
    * 193.47.147.58           polesw1
    * 193.47.147.59           polepdu1
    * 193.47.147.60           poleups1
  * **193.47.147.64/27**          Outdoor - garden, treehouse, logstore etc
    * 193.47.147.65           VLAN gateway sw1
    * 193.47.147.66           
    * 193.47.147.67           
    * 193.47.147.68           
    * 193.47.147.80           DHCP
    * ...
    * 193.47.147.94           DHCP
  * **193.47.147.96/27**          House
    * 193.47.147.97           VLAN gateway
    * 193.47.147.98           
    * 193.47.147.110          DHCP
    * ...
    * 193.47.147.127          DHCP
  * **193.47.147.128/27**         Office
    * 193.47.147.129 
    * 193.47.147.130          
    * 193.47.147.131          
    * 193.47.147.132          printer (DHCP)
    * 193.47.147.133          pdu1 (DHCP)
    * 193.47.147.134          swloft1
    * 193.47.147.140          DHCP
    * ...
    * 193.47.147.158          DHCP
  * **193.47.147.160/27**         Workshop, barn and shed
    * 193.47.147.161          VLAN gateway sw1
    * 193.47.147.162          barnsw1
    * 193.47.147.163          barnsw1
    * 193.47.147.164          workshopsw1
    * 193.47.147.165          pdushed1
    * 193.47.147.166          upsshed1
    * 193.47.147.167          pdubarn1
    * 193.47.147.168          upsbarn1
    * 193.47.147.169          pirelay1
    * 193.47.147.170          pirelay2
    * 193.47.147.171          cctvnvr1
    * 193.47.147.180          DHCP
    * ...
    * 193.47.147.190          DHCP
  * **193.47.147.192/26**         Wireless clients, SSID: Llwyn Y Gorras
    * 193.47.147.193          VLAN gateway
    * 193.47.147.196 - 254    DHCP

* 10.76.0.0/16
  * 10.76.11.0/24     VLAN 11 - Power management, UPS/PDUs
  * 10.76.12.0/24     VLAN 12 - Switch management
  * 10.76.13.0/24     VLAN 13 - Unifi APs
  * VLAN14 - home wifi users
  * 10.76.15.0/24     VLAN15  - guest wifi users
  * 10.76.16.0/24     VLAN 16 - IOT
  * 10.76.31.0/24     VLAN 31 - CCTV  
  * 10.76.32.0/24     VLAN 32 - Cisco APs
  * 10.76.33.0/24     temp nat'd on rt3
  * 10.76.34.0/24     VPN users
  * 10.76.200.0/23    Docker containers - covering prefixes - /32s via CRoHDAd
     * 10.76.200.1-9  web test boxes
     * 10.76.200.10   nodered
     * 10.76.200.11   mqtt
     * 10.76.200.12   homenms
     * 10.76.200.13   homenms-db
     * 10.76.200.14   caddy dst-nat'd behind 193.47.147.6
     * 10.76.200.15   portainer - portainer.home.nat.ms
     * 10.76.200.16   homeassistant - ha.home.nat.ms
     * 10.76.200.17   influxdb
     * 10.76.200.18   grafana
     * 10.76.200.19   ?
     * 10.76.200.20   ?
     * 10.76.200.21   iocontroller home
     * 10.76.200.30   atlas-home
     * 10.76.200.31   atlas-dyfedit
     * 10.76.200.32   atlas-faelix
     * 10.76.200.33   atlas-aaisp
     * 10.76.200.34   atlas-vodafone
  


```
2001:67c:1b40::/46 cover
2001:67c:1b40::/48 home
2001:67c:1b40::3/128
2001:67c:1b40:1::/64  linknets - as /112s
2001:67c:1b40:1:1::/112 sw1-rt3

```
