# Home IP Plan

Home AS30746, transit provided by AS41495 and AS60036.

Dev AS56817 is behind AS30746, single router for RouterOS 7 testing.

## Prefixes

IPv4

| Prefix              | Originated  | RIR           | Type       | Notes                                                      |
|---------------------|------------ |---------------|------------|------------------------------------------------------------|
| 44.131.40.0/24      | AS30746     |   AMPRnet     |  Assigned  | Home amateur radio space  (not my asset)                   |
| 91.232.181.0/24     | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2022 in exchange for £   |
| 130.193.78.0/24     | AS49396     |   RIPE        |  PA        | Unsued                                                     |   
| 185.19.148.0/23     | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2022 in exchange for £   |
| 185.19.150.0/24     | AS20712     |   RIPE        |  PA        | Loaned TXRX in exchange for 2 x 1G FTTP                    |
| 185.19.151.0/24     | AS57436     |   RIPE        |  PA        | Loaned to Sameer Abdel-Hafez for free                      |
| 185.61.112.0/24     | AS56817     |   RIPE        |  PA        | Home network - RouterOS 7 testing                          |
| 185.61.113.0/24     | AS30746     |   RIPE        |  PA        | Home network - unused                                      |
| 185.61.114.0/22     | AS30746     |   RIPE        |  PA        | Home network - guests                                      |
| 185.61.115.0/24     | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2022 in exchange for £   |
| 193.47.147.0/24     | AS30746     |   RIPE        |  PI        | Home network - services, NAT behind                        |
| 195.177.252.0/23    | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2022 in exchange for £   |

IPv6

| Prefix              | Originated  | RIR           | Type       | Notes                                                      |
|---------------------|------------ |---------------|------------|------------------------------------------------------------|
| 2a04:ebc0::/29      | AS30746     |   RIPE        |  PA        | Home                                                       |
| 2a04:ec40::/29      | AS30746     |   RIPE        |  PA        | Lab and other things                                       |
| 2a11:9d80::/29      | AS49396     |   RIPE        |  PA        | LYG                                                        |
  
## Llwynygorras

`130.193.78.0/24`
`2a11:9d80::/29`

```
49396:1000            Route recieved from transit
49396:1001               from Dyfed IT Castlemorris 1G
49396:1002               from Dyfed IT Llwynygorras 1G
49396:1003               from TXRX 1G A
49396:1004               from TXRX 1G B

49396:2000            Route recieved from downstream
49396:2001               from Nat A
49396:2200               ... announce to transit

49396:3000            Advertised via transit, set outbound to transit providers
49396:3001               via Dyfed IT Castlemorris 1G
49396:3002               via Dyfed IT Llwynygorras 1G
49396:3003               via TXRX 1G A
49396:3004               via TXRX 1G B
49396:3100               ... originated prefix
49396:3200               ... from downstream

49396:4000            Route locally originated
```

```
130.193.78.0/24
    130.193.78.1/32   gateway loopback              2a11:9d80:1::1/128
    130.193.78.56/30  Nat BGP                       2a11:9d80:2:1::1/64
    130.193.78.64/29  Nat DHCP          VLAN 101    2a11:9d80:3:1::1/64  &  PD 2a11:9d80:a101::/48
    130.193.78.72/29  Ryans DHCP        VLAN 102    2a11:9d80:3:2::1/64  &  PD 2a11:9d80:a102::/48
    130.193.78.80/29  Neil DHCP         VLAN 103    2a11:9d80:3:3::1/64  &  PD 2a11:9d80:a103::/48
    130.193.78.88/29  Watkins DHCP      VLAN 104    2a11:9d80:3:4::1/64  &  PD 2a11:9d80:a104::/48
    130.193.67.96/29  Greg DHCP         VLAN 105    2a11:9d80:3:5::1/64  &  PD 2a11:9d80:a105::/48
```

## AS56817 sausages.home.nat.ms

RB3011 for RouterOS 7.x testing, downstream from AS30746

`185.61.112.0/24`


## BGP communities

```
30746:668             Route recieved from UTRS blackhole service

30746:1000            Route recieved from transit
30746:1001               from Dyfed IT Castlemorris 1G
30746:1002               from Dyfed IT Llwynygorras 1G
30746:1004               from FAELIX tunnel
30746:1005               from Llwynygorras

30746:8000            Advertised
30746:8001               via Dyfed IT Castlemorris
30746:8002               via Dyfed IT Llwynygorras
30746:8005               via LLwynygorras

30746:5000            Route recieved from a hypervisor
30746:5101               from moby1                          *
30746:5102               from moby2                          *
30746:5103               from moby3                          *
```

## Public assignments

```
193.47.147.0/24
    193.47.147.1              rt1.home.nat.ms loopback
    193.47.147.2
    193.47.147.3
    193.47.147.4
    193.47.147.5              NAT dst-nat Wireguard
    193.47.147.6              NAT dst-nat Caddy reverse proxy
    193.47.147.7              old - MQTT broker
    193.47.147.8              NAT dst-nat DNS resolver 1
    193.47.147.9              NAT dst-nat DNS resolver 2
    193.47.147.10             
    193.47.147.11             
    193.47.147.12             
    193.47.147.13             NAT src-nat VPN L2TP users
    193.47.147.14             NAT src-nat home              10.76.14.0/24
    193.47.147.15             NAT src-nat mgmt              10.76.10.0/24
    193.47.147.16             NAT src-nat iot               10.76.16.0/24
    193.47.147.17             NAT src-nat cctv              10.76.17.0/24
    193.47.147.18             NAT src-nat LibreNMS          10.76.200.12
    193.47.147.19             NAT dst-nat Unifi Controller  10.76.200.20
    193.47.147.20             NAT dst-nat NTP on ADSP Pi
    193.47.147.21             NAT dst-nat frigate1
    193.47.147.22             NAT dst-nat Unifi Controller old
    193.47.147.24/30
        193.47.147.25         rt1
        193.47.147.26         rt2
    193.47.147.28/30
    193.47.147.32/29
        193.47.147.33         rt1
        193.47.147.34         moby1     AS64512
    193.47.147.40/29
        193.47.147.41         rt1
        193.47.147.42         pve1
        193.47.147.43         pve1-ipmi
    193.47.147.48/29
        193.47.147.49         rt1
        193.47.147.50         minimoby1  pi4 8gb w/SSD
        193.47.147.51         minimoby2  pi4 8gb w/SSD
        193.47.147.52         minimoby3  pi4 2gb SD card
        193.47.147.54         fatmoby1   i7 4c 32gb nuc
    ...
    193.47.147.248/29
        193.47.147.251        tor-relay1
        193.47.147.252        tor-relay2
```

## Private assignments

```
10.76.0.0/16
    10.76.10.0/24             VLAN 10 - Management; APs, PDUs, UPSs, Switches
    10.76.11.0/24             VLAN 11 - Old powermgmt, still has some UPSs on it
    10.76.14.0/24             VLAN 14 - Home
    10.76.16.0/24             VLAN 16 - IOT devices
    10.76.18.0/24             VLAN 18 - Vodafone LTE routed via SXTLTE
    10.76.31.0/24             VLAN 31 - CCTV cameras
    10.76.50.0/24             VLAN 50 - Containers on PIs
     * 10.76.50.5             wireguard                     minimoby3
     * 10.76.50.11            dns1                          minimoby1
     * 10.76.50.12            dns2                          minimoby3
     * 10.76.50.13            mqtt                          minimoby1
     * 10.76.50.14            home assistant                minimoby1   via caddy
     * 10.76.50.15            portainer                     minimoby1   via caddy
     * 10.76.50.16            caddy                         minimoby1
     * 10.76.50.17            ioctl-home                    minimoby1
     * 10.76.50.18            frigate1                      minimoby2
     * 10.76.50.19            grafana                       minimoby2
     * 10.76.50.20            unifi                         minimoby1
     * 10.76.50.21            adsb2influxdb                 minimoby2
     * 10.76.50.22            nodered                       minimoby1
     * 10.76.50.23            influxdb                      minimoby2
     * 10.76.50.24            homenms                       minimoby2
     * 10.76.50.25            homenms-db                    minimoby2
     * 10.76.50.26            homenms-rrdcached             minimoby2
     
     
     * 10.76.50.192/29    home
       * 10.76.50.193     telegraf-home                     minimoby1
     * 10.76.50.200/29    dyfedit1 (castlemorris)
       * 10.76.50.201     telegraph-dyfedit1
     * 10.76.50.208/29    dyfedit2 (llwynygorras)
       * 10.76.50.209     telegraph-dyfedit2
     * 10.76.50.216/29    dyfeditpppoe (llwynygorras)
       * 10.76.50.217     telegraph-dyfeditpppoe
     * 10.76.50.224/29    vodafone
     * 10.76.50.232/29    faelix (tunnel over vodafone)
       * 10.76.50.233     telegraf-faelix
     * 10.76.50.254       tor-relay-3 src/dst-nat to 195.177.252.5 pppoe      

```


```
2001:67c:1b40::/46 cover
2001:67c:1b40::/48 home
2001:67c:1b40::3/128
2001:67c:1b40:1::/64  linknets - as /112s
2001:67c:1b40:1:1::/112 sw1-rt3

```
