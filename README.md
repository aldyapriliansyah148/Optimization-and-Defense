# Optimization-and-Defense
 Perancangan Infrastruktur Zero-Trust Access Control dan VLAN Hardening pada Jaringan Multi-Department
 Perangkat Jaringan (Network Devices)
1 Unit Switch Layer 3 (L3 Switch)
1 Unit Switch Layer 2 (L2 Switch)
1 Unit Router
PC atau Laptop (Minimal 4 Unit):

Optimization and Defense: Perancangan Infrastruktur Zero-Trust Access Control dan VLAN Hardening pada Jaringan Multi-Department
Gambaran Proyek: Mengimplementasikan konsep keamanan modern (Zero-Trust) di tingkat jaringan lokal. Proyek ini memisahkan trafik antar-departemen (HR, Finance, IT, Guest) dan memastikan perangkat yang tidak dikenal langsung diblokir secara otomatis oleh switch.
Fitur & Teknologi yang Digunakan:
Network Hardening: Port Security (Sticky MAC & Violate Mode Drop/Shutdown).
Traffic Isolation: VLAN & Inter-VLAN Routing (Router-on-a-Stick atau Switch Layer 3).
Filtering: Extended ACL (memodelkan hak akses spesifik, misal: Dept Guest hanya bisa akses internet, Dept Finance tidak bisa di-ping dari Dept HR).
Mitigasi Serangan: DHCP Snooping & Dynamic ARP Inspection (DAI).
