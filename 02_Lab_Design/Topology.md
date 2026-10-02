# Initial Topology

```text
                         INTERNET
                             |
                             v
                      +-------------+
                      |   pfSense   |
                      |  Firewall   |
                      +------+------+
                             |
                  +----------+----------+
                  |                     |
               VLAN 10                VLAN 20
             Internal LAN             Servers
                  |                     |
             +----+----+           +----+------+
             | Windows |           |  Ubuntu   |
             | Client  |           |  Server   |
             +---------+           +-----------+
                                       |
                              +--------+--------+
                              |                 |
                         +----v----+       +----v----+
                         | Suricata|       |  Wazuh  |
                         | IDS/IPS |       |   SIEM  |
                         +---------+       +---------+
```

## Important design note
Suricata and Wazuh will not necessarily sit literally in-line after the Windows client. Their final placement will be decided during implementation based on the virtualization design and available hardware.
