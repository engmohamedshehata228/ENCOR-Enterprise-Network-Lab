Overview
This project demonstrates a real-world enterprise network deployed on Cisco Packet Tracer. The design includes a Headquarter and two remote branches connected through an ISP using NAT overload and Site-to-Site IPsec VPN tunnels instead of any routing protocol.
The network uses 8 departmental VLANs, wireless coverage per floor using wireless switches, centralized DHCP on the core L3 switch, strict access control using extended ACLs, port security, and LACP EtherChannel between L2 and L3 switches.

Topology & VLANs
Branches: Headquarter + 2 Remote Sites (each site connected individually to the ISP using static default routes, NAT, and VPN tunnels).

VLANs (8):
Customer Service
Operations
Marketing
Sales
Accounting
HR
IT
Management
Inter-VLAN routing: Layer-3 Core Switch (SVIs configured per VLAN)

Wireless & Access
Each floor is equipped with two wireless switches (access point aggregators) connected to the access/distribution switches.
Wireless switches map clients to the appropriate VLANs so wireless users obtain the same access privileges as wired devices.

Wireless switches per floor: 2
SSID & VLAN mapping: Each SSID is assigned to its corresponding department VLAN
Routing & Services
No routing protocol used
Branches connect via the ISP using static default routes → ISP
NAT overload (PAT) enabled on each branch edge router for external access
Site-to-Site VPN (IPsec) used to securely connect HQ with the two branches
DHCP centralized on the L3 core switch (separate pool for each VLAN)
Internal networks are routed locally only (no NAT inside the LAN)

Security
ACLs
Extended ACLs enforce strict access control:
IT department: full access and administrative SSH to all devices.
Branch Managers + IT: allowed HTTP/HTTPS access to the Internet.
FTP & TFTP: IT only.
Final rule: permit ip any any for normal internal communication.

Port Security
Port Security is configured on access ports to limit MAC addresses per port, preventing unauthorized devices or spoofing. Ports react with restrict or shutdown depending on the policy.

Performance & Redundancy
EtherChannel (LACP) implemented between Layer-2 and Layer-3 switches for redundancy and higher bandwidth
Hierarchical design (Core / Distribution / Access) for scalability and fault isolation
