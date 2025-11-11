# Summary
This Cisco IOS switch configuration has several security and best practice issues that need to be addressed.

# Inventory
* Device: Cisco IOS switch
* Software version: 15.0
* Interfaces:
	+ FastEthernet0/1-24
	+ GigabitEthernet0/1-2
	+ Vlan1

# Findings

### Security Controls

* **AAA**: Not configured (Severity: medium)
* **Enable secret**: Configured, but not recommended to use 5-character hash (Severity: low)
* **VTY/SSH**: SSH only, no Telnet (Severity: low)
* **Logging/Timestamps**:
	+ No service timestamps log datetime msec (Severity: high)
	+ No service timestamps debug datetime msec (Severity: high)
* **Password Encryption**: Configured (Severity: low)

### L2 Safety

* **STP Mode/Guards**: PVST mode, but no BPDU Guard configured (Severity: medium)
* **PortFast on Access Ports**: Not configured (Severity: medium)
* **Storm-Control**: Not configured (Severity: medium)

### VLAN Hygiene

* **Declared vs Used VLANs**: 10 VLANs declared, but only 5 used (Severity: low)
* **Native VLAN**: Native VLAN set to 666, which is not a standard VLAN (Severity: high)
* **Management SVI**: Vlan1 configured as management SVI, but no IP address assigned (Severity: medium)

### Access Port Hygiene

* **Port Descriptions**: Not configured (Severity: low)
* **Shutdown Unused Ports**: FastEthernet0/6-10 shutdown, but not documented (Severity: low)

### Remote Management

* **SSH Only**: SSH only, no Telnet (Severity: low)
* **Login Method**: Local login only (Severity: medium)

# Recommended Fixes

### Security Controls

* Configure AAA using local database or external server
* Change enable secret to a stronger password
* Enable service timestamps log datetime msec and debug datetime msec

### L2 Safety

* Configure BPDU Guard on all trunk ports
* Enable PortFast on access ports
* Configure Storm-Control on all interfaces

### VLAN Hygiene

* Remove unused VLANs (5-10)
* Change native VLAN to a standard VLAN (e.g. 1)
* Assign an IP address to Vlan1

### Access Port Hygiene

* Document shutdown of FastEthernet0/6-10
* Configure port descriptions for all interfaces

### Remote Management

* No changes needed, SSH only is already configured

# Verification Steps

1. Verify AAA configuration using `show running-config` and `debug aaa`
2. Check enable secret strength using `enable secret <new-password>`
3. Enable service timestamps log datetime msec and debug datetime msec using `service timestamps log datetime msec` and `service timestamps debug datetime msec`
4. Configure BPDU Guard on all trunk ports using `spanning-tree bpduguard default`
5. Enable PortFast on access ports using `spanning-tree portfast trunk`
6. Configure Storm-Control on all interfaces using `storm-control action shutdown`
7. Remove unused VLANs (5-10) using `vlan database` and `no vlan <vlan-id>`
8. Change native VLAN to a standard VLAN (e.g. 1) using `switchport trunk native vlan 1`
9. Assign an IP address to Vlan1 using `ip address <ip-address> secondary`

# Appendix (Key Snippets)

* `service password-encryption` (password encryption)
* `spanning-tree mode pvst` (STP mode)
* `spanning-tree extend system-id` (STP extend system ID)
* `line vty 0 4 login` and `line vty 5 15 login` (VTY/SSH configuration)
