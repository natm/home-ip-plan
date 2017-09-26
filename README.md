# Home IP Plan

Home AS number, transit provided by AS60036

* 193.47.147.0/24             Covering prefix
  * **193.47.147.0/28**           Loopbacks and /32's
    * 193.47.147.1            rt1.home.nat.ms
    * 193.47.147.2            sw1.home.nat.ms
    * 193.47.147.14           NAT src CCTV
    * 193.47.147.15           NAT src Wifi APs
  * **193.47.147.16/28**          Linknets
    * 193.47.147.16/30        rt1-sw1
      * 193.47.147.17         eth4.rt1
      * 193.47.147.18         x.sw1
    * 193.47.147.20/30        sw1-wlc
      * 193.47.147.21         sw1
      * 193.47.147.22         wlc
    * 193.47.147.24/30
      * 193.47.147.25         sw1
      * 193.47.147.26         host
    * 193.47.147.28/30
  * **193.47.147.32/28**          Linknets
    * 193.47.147.32/30
    * 193.47.147.36/30
    * 193.47.147.40/30
    * 193.47.147.44/30
  * **193.47.147.56/29**          Pole
    * 193.47.147.57           sw1
    * 193.47.147.58           polesw1
    * 193.47.147.59           polepdu1
    * 193.47.147.60           poleups1
  * **193.47.147.64/27**          Outdoor - garden, treehouse, logstore etc
  * **193.47.147.96/27**          House
    * 193.47.147.110          DHCP
    * ...
    * 193.47.147.127          DHCP
  * **193.47.147.128/27**         Office
    * 193.47.147.129 
    * 193.47.147.130          officesw1 (static)
    * 193.47.147.131          officesw2 (static)
    * 193.47.147.132          printer (DHCP)
    * 193.47.147.133          pdu1 (DHCP)
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
  * 10.76.31.0/24     VLAN 31 - CCTV
  * 10.76.32.0/24     VLAN 32 - Wifi APs
