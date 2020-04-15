# Experimental Configlets

Very rudimentary examples not tested as part of our QA process.  Modifying to your environment and testing the payloads absolutely necessary.

For more detailed information refer to [Configlet READ.md](../README.md)


# Experimental Examples
Configlet examples in `payloads` are in JSON format. 

Configlets that affect numbered interfaces (native_vlan.json) or existing routing process IDs (static_routes.json) must be edited to match the device details of your environment.  Otherwise, they will not work properly. 

---

| Configlet          | OS         | Use                                                                                                      |
| ------------------ | ---------- | -------------------------------------------------------------------------------------------------------- |
| native_vlan.json   | EOS        | Change the native vlan on a port                                                                         |
| ntp.json           | EOS        | Clock and NTP server                                                                                     |
| snmp.json          | NX-OS, EOS | SNMP Server Configuration                                                                                |
| spanning_tree.json | NX-OS      | Enable Spanning Tree and priority                                                                        |
| ssh_config.json    | NX-OS, EOS | Console and timeout settings                                                                             |
| static_routes.json | NX-OS      | Create static routes with VRFs.  Used when the upstream device doesn't support dynamic routing protocols |
| syslog.json        | NX-OS, EOS | Trap and logging configuration                                                                           |
| tacacs.json        | NX-OS, EOS | TACACS and AAA configuration                                                                             |


> **NOTES**:
> 1. Passwords and other secret keys are not encrypted in Configlets.
> 2. You can use the same Configlets across the entire enterprise, but it’s a good idea to create regionally specific Property Sets.
> 3. Avoid using shortened versions of commands. 

---

# How to use
1. Customize the JSON files to meet your specific deployment
2. Test Configlet templates and negation templates on a separate dedicated device.
3. Create the new configlet via `POST` to AOS API 
```
/api/design/configlets
```
