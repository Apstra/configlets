# AOS Configlets

Configlets are configuration templates that are applied to network devices. They augment the AOS Reference Design with non-native device configuration.

Some use case examples include:

1. Syslog
2. SNMP access policy
3. TACACS / RADIUS
4. Management ACLs
5. NTP

For more detailed information refer to [Configlet Overview & Concepts in AOS Documentation](https://portal.apstra.com/docs/design_phase_concepts.html#configlets)

Configlets are composed of two parts.

## Template Text

CLI commands to add custom configuration to a device. Contents are not validated by AOS.

## Negation Template Text

CLI commands to disable functionality of the Configlet (not applicable to File Configlets). Contents are not validated by AOS.

For example, if the Template Text is `username example privilege 15 secret 0 MyPassword`, the Negation Text might be `no username example`.

Template Text and Negation Template Text are **not** validated by AOS. They are issued directly to the devices. If you improperly configure a Configlet, AOS does not raise warnings or restrictions. To ensure that a Configlet performs exactly as intended, test Configlet templates and negation templates on a separate dedicated device.

# Configlet Examples
in `payloads` are known working and tested configlet examples in JSON format. Configlets that affect numbered interfaces (native_vlan.json) or existing routing processes (static_routes.json) must be edited to match the device details of your environment. 

* native_vlan.json
  * EOS
* ntp.json
  * EOS
* snmp.json
  * NX-OS, EOS
* spanning_tree.json
  * NX-OS
* ssh_config.json
  * NX-OS, EOS
* static_routes.json
  * NX-OS
* syslog.json
  * NX-OS, EOS
* tacacs.json
  * NX-OS, EOS

# How to use
1. Customize the JSON files to meet your specific deployment
2. Create the new configlet via `POST` to AOS API 
```
/api/design/configlets
```
