# Home IP Plan

Home AS30746, transit provided by AS41495 and AS60036.

Dev AS56817 is behind AS30746, single router for RouterOS 7 testing.

## Prefixes

| Prefix              | Originated  | RIR           | Type       | Notes                                    |
|---------------------|------------ |---------------|------------|------------------------------------------|
| 44.131.40.0/24      | AS30746     |   AMPRnet     |  Assigned  | Home amateur radio space                 |
| 91.232.181.0/24     | AS60036     |   RIPE        |  PA        | Loaded to Dyfed IT until August 2020     |
| 185.19.148.0/23     | AS60036     |   RIPE        |  PA        | Loaded to Dyfed IT until August 2020     |
| 185.19.150.0/24     | AS20712     |   RIPE        |  PA        | Friends and family AAISP FTTC lines      |
| 185.19.151.0/24     | AS57436     |   RIPE        |  PA        | Loaned to Sameer Abdel-Hafez             |
| 185.61.112.0/24     | AS56817     |   RIPE        |  PA        | Home network - RouterOS 7 testing        |
| 185.61.113.0/24     | AS30746     |   RIPE        |  PA        | Home network - unused                    |
| 185.61.114.0/22     | AS30746     |   RIPE        |  PA        | Home network - guests                    |
| 185.61.115.0/24     | AS60036     |   RIPE        |  PA        | Loaned to Dyfed IT until August 2020     |
| 193.47.147.0/24     | AS30746     |   RIPE        |  PI        | Home network                             |
| 195.177.252.0/23    | AS60036     |   RIPE        |  PA        | Loaned to Dyfed IT until August 2020     |



## Assignments:

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
      * 193.47.147.25         rt1
      * 193.47.147.26         rt2
    * 193.47.147.28/30
      * 193.47.147.29         rt2
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
  * **193.47.147.56/29**
  * **193.47.147.64/27**
  * **193.47.147.96/27**
  * **193.47.147.128/27**         Office
    * 193.47.147.129          rt1
    * 193.47.147.132          printer (DHCP)
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
     * 10.76.200.22   frigate1
     * 10.76.200.23   frigate2
     * 10.76.200.30   atlas-home
     * 10.76.200.31   atlas-dyfedit   (on BGP ext interface)
     * 10.76.200.32   atlas-faelix
     * 10.76.200.33   atlas-aaisp
     * 10.76.200.34   atlas-vodafone
     * 10.76.200.35   atlas-dyfedit2  (on independant pppoe conn)
     * 10.76.200.40   telegraf-home
     * 10.76.200.41   telegraf-dyfedit   (on BGP ext interface)
     * 10.76.200.42   telegraf-faelix
     * 10.76.200.43   telegraf-aaisp
     * 10.76.200.44   telegraf-vodafone
     * 10.76.200.45   telegraf-dyfedit2  (on independant pppoe conn)
     

```
2001:67c:1b40::/46 cover
2001:67c:1b40::/48 home
2001:67c:1b40::3/128
2001:67c:1b40:1::/64  linknets - as /112s
2001:67c:1b40:1:1::/112 sw1-rt3

```
