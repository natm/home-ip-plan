# Home IP Plan

Home AS30746, transit provided by AS41495 and AS60036.

Dev AS56817 is behind AS30746, single router for RouterOS 7 testing.

## Prefixes

| Prefix              | Originated  | RIR           | Type       | Notes                                    |
|---------------------|------------ |---------------|------------|------------------------------------------|
| 44.131.40.0/24      | AS30746     |   AMPRnet     |  Assigned  | Home amateur radio space                 |
| 91.232.181.0/24     | AS60036     |   RIPE        |  PA        | Loaded to Voneus PLC until August 2021     |
| 130.193.78.0/24     | AS49396     |   RIPE        |  PA        | Unused                                   |   
| 185.19.148.0/23     | AS60036     |   RIPE        |  PA        | Loaded to Voneus PLC until August 2021     |
| 185.19.150.0/24     | AS20712     |   RIPE        |  PA        | Friends and family AAISP FTTC lines      |
| 185.19.151.0/24     | AS57436     |   RIPE        |  PA        | Loaned to Sameer Abdel-Hafez             |
| 185.61.112.0/24     | AS56817     |   RIPE        |  PA        | Home network - RouterOS 7 testing        |
| 185.61.113.0/24     | AS30746     |   RIPE        |  PA        | Home network - unused                    |
| 185.61.114.0/22     | AS30746     |   RIPE        |  PA        | Home network - guests                    |
| 185.61.115.0/24     | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2021     |
| 193.47.147.0/24     | AS30746     |   RIPE        |  PI        | Home network                             |
| 195.177.252.0/23    | AS60036     |   RIPE        |  PA        | Loaned to Voneus PLC until August 2021     |


## BGP communities

```
30746:668             Route recieved from UTRS blackhole service

30746:1000            Route recieved from transit
30746:1001               from Dyfed IT Castlemorris 1G
30746:1002               from Dyfed IT Llwynygorras 1G
30746:1004               from FAELIX tunnel

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
    193.47.147.5
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
    193.47.147.160/27
        193.47.147.161        rt1
        193.47.147.164        workshopsw1
        193.47.147.169        pirelay1
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
     
    10.76.200.0/23            Docker containers, routed via moby hypervisors VMs, /32s via CROHDAD
        10.76.200.10          nodered
        10.76.200.12          homenms
        10.76.200.13          homenms-db        
     * 10.76.200.17   influxdb
     * 10.76.200.19   ?
     * 10.76.200.20   ?
     * 10.76.200.24   adsb2influxdb
     * 10.76.200.40   telegraf-home
     * 10.76.200.41   telegraf-dyfedit   (on BGP ext interface)
     * 10.76.200.42   telegraf-faelix
     * 10.76.200.43   telegraf-aaisp
     * 10.76.200.44   telegraf-vodafone
     * 10.76.200.45   telegraf-dyfedit2  (on independant pppoe conn)
     * 10.76.200.200/29    dyfedit1 (castlemorris)
       * 10.76.200.201 telegraph-dyfedit1
     * 10.76.200.208/29    dyfedit2 (llwynygorras)
       * 10.76.200.209 telegraph-dyfedit2
     * 10.76.200.216/29    dyfeditpppoe (llwynygorras)
       * 10.76.200.217 telegraph-dyfeditpppoe
     * 10.76.200.224/29    vodafone
     * 10.76.200.232/29    faelix (tunnel over vodafone)
     * 10.76.200.240/29
     * 10.76.200.248/29    No routing_mark
       * 10.76.200.249 telegraf-home
```


```
2001:67c:1b40::/46 cover
2001:67c:1b40::/48 home
2001:67c:1b40::3/128
2001:67c:1b40:1::/64  linknets - as /112s
2001:67c:1b40:1:1::/112 sw1-rt3

```
