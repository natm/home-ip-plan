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
30746:5104               from moby4                          *
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
    193.47.147.8              Container DNS resolver 1
    193.47.147.9              Container DNS resolver 2
    193.47.147.10             old - syslog
    193.47.147.11             old - ntp/sntp
    193.47.147.12             
    193.47.147.13             NAT src-nat VPN L2TP users
    193.47.147.14             NAT src-nat home              10.76.14.0/24
    193.47.147.15             NAT src-nat mgmt              10.76.10.0/24
    193.47.147.16             NAT src-nat iot               10.76.16.0/24
    193.47.147.17             NAT src-nat cctv              10.76.17.0/24
    193.47.147.18             NAT src-nat LibreNMS          10.76.200.12
    193.47.147.19             NAT dst-nat Unifi Controller  10.76.200.20
    193.47.147.20             NAT dst-nat NTP on ADSP Pi
    193.47.147.24/30
        193.47.147.25         rt1
        193.47.147.26         rt2
    193.47.147.28/30
    193.47.147.32/29
        193.47.147.33         rt1
        193.47.147.34         moby1     AS64512
        193.47.147.35         moby2     AS64512
        193.47.147.36         moby3     AS64512
        193.47.147.37         moby3     AS64512
    193.47.147.40/29
        193.47.147.41         rt1
        193.47.147.42         pve1
        193.47.147.43         pve1-ipmi
    193.47.147.48/29
        193.47.147.49         rt1
        193.47.147.50         minimoby1
    ...
    193.47.147.160/27
        193.47.147.161        rt1
        193.47.147.164        workshopsw1
        193.47.147.169        pirelay1
        193.47.147.170        pirelay2
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
     * 10.76.50.12            resolver2            
    10.76.200.0/23            Docker containers, routed via moby hypervisors VMs, /32s via CROHDAD
        10.76.200.1-9         web test boxes
        10.76.200.10          nodered
        10.76.200.11          mqtt
        10.76.200.12          homenms
        10.76.200.13          homenms-db
        10.76.200.14          caddy dst-nat'd behind 193.47.147.6
        10.76.200.15          portainer - via caddy portainer.home.nat.ms
        10.76.200.16          homeassistant - via caddy ha.home.nat.ms
     * 10.76.200.17   influxdb
     * 10.76.200.18   grafana
     * 10.76.200.19   ?
     * 10.76.200.20   ?
     * 10.76.200.21   iocontroller home
     * 10.76.200.22   frigate1
     * 10.76.200.23   frigate2
     * 10.76.200.24   adsb2influxdb
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
     * 10.76.200.101  honeygain1
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
       * 10.76.200.248 atlas-home
       * 10.76.200.249 telegraf-home
```


```
2001:67c:1b40::/46 cover
2001:67c:1b40::/48 home
2001:67c:1b40::3/128
2001:67c:1b40:1::/64  linknets - as /112s
2001:67c:1b40:1:1::/112 sw1-rt3

```
