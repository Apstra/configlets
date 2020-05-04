# Experimental Configlets

Very rudimentary examples not tested as part of our QA process.  Modifying to your environment and testing the payloads absolutely necessary.

For more detailed information refer to [Configlet READ.md](../README.md)


# Experimental Examples
Configlet examples in `configlets-payloads` and `property-sets-payloads` are in JSON format. 

Configlets that affect numbered interfaces (native_vlan.json) or existing routing process IDs (static_routes.json) must be edited to match the device details of your environment.  Otherwise, they will not work properly. 

---

| Configlet              | Depends on Property-Sets   | NX-OS   | EOS     | CLN     | Juniper | Use                                                                                                       |
| ---------------------- | ---------------------------| ------- | ------- | ------- | ------- | --------------------------------------------------------------------------------------------------------- |
| ative_vlan.json        | No                         |         | Y       |         |         | Change the native vlan on a port.                                                                         |
| ntp.json               | ntp-set.json               |         | Y       | Y       |         | Clock and NTP server.                                                                                     |
| snmp.json              | No                         | Y       | Y       |         |         | SNMP Server Configuration.                                                                                |
| spanning_tree.json     | No                         | Y       |         |         |         | Enable Spanning Tree and priority.                                                                        |
| ssh_config.json        | No                         | Y       | Y       |         |         | Console and timeout settings.                                                                             |
| static_routes.json     | No                         | Y       |         |         |         | Create static routes with VRFs. Used when the upstream device doesn't support dynamic routing protocols   |
| syslog.json            | No                         | Y       | Y       |         |         | Trap and logging configuration.                                                                           |
| tacacs.json            | No                         | Y       | Y       |         |         | TACACS and AAA configuration.                                                                             |
| mgmt_vrf_services.json | mgmt_vrf_services-set.json |         |         | Y       |         | Restrict Services in Mgmt VRF.                                                                            |


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
4. Optionnaly, create the new property-sets via `POST` to AOS API 
```
/api/property-sets
```