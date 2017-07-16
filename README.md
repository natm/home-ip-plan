# Home IP Plan

Home AS number, transit provided by AS60036

Need to migrate out of 185.61.112.0/23

* 193.47.147.0/24             Covering prefix
  * 193.47.147.0/28           Loopbacks and /32's
    * 193.47.147.1            rt1.home.nat.ms
    * 193.47.147.2            sw1.home.nat.ms
  * 193.47.147.16/28          Linknets
    * 193.47.147.16/30        rt1-sw1
      * 193.47.147.17         eth4.rt1
      * 193.47.147.18         x.sw1
    * 193.47.147.20/30
    * 193.47.147.24/30
    * 193.47.147.28/30
  * 194.47.147.32/28          Linknets
    * 194.47.147.32/30
    * 194.47.147.36/30
    * 194.47.147.40/30
    * 194.47.147.44/30
  * 193.47.147.192/26         Wireless clients, SSID: Llwyn Y Gorras
    * 193.47.147.193          VLAN gateway
    * 193.47.147.196 - 254    DHCP
