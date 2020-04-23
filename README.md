# Repo Information  
**Summary**

| Folder       | Summary                                                                                                                                       |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Stable       | Past rigorous QA without any known serious issues reported.  Still requires modifying to match your precise deployment.                       |
| Experimental | Very rudimentary examples not tested as part of our QA process.  Modifying to your environment and testing the payloads absolutely necessary. |



# AOS Configlets

Configlets are configuration templates that are applied to network devices. They augment the AOS Reference Design with native device configuration.  

A Configlet is a powerful tool that provides Apstra AOS customers the freedom to implement features or capabilities not yet modeled in AOS.  This gives AOS a significant advantage over competitive solutions or SDN controller-based offerings where enhancements or feature requests would take months to years to implement.  With a few hours or days of testing, customers can use Configlets to address new use cases or features.  

However, with great ability comes great responsibility.  Untested or malcrafted Configlets can cause deployment failures and potentially service impacting failures.  It's the customer's responsibility to test experimental or custom Configlets to ensure they operate correctly. 

## Use Cases
Some use case examples include:

1. Syslog
2. SNMP access policy
3. TACACS / RADIUS
4. Management ACLs
5. NTP

For more detailed information refer to [Configlet Overview & Concepts in AOS Documentation](https://portal.apstra.com/docs/design_phase_concepts.html#configlets)

# Configlet Components


## Template Text

CLI commands to add custom configuration to a device. Contents are not validated by AOS.

## Negation Template Text

CLI commands to disable functionality of the Configlet (not applicable to File Configlets). Contents are not validated by AOS.

For example, if the Template Text is `username example privilege 15 secret 0 MyPassword`, the Negation Text might be `no username example`.

Template Text and Negation Template Text are **not** validated by AOS. They are issued directly to the devices. If you improperly configure a Configlet, AOS does not raise warnings or restrictions. To ensure that a Configlet performs exactly as intended, test Configlet templates and negation templates on a separate dedicated device.

## Property Sets
***Optional***  A collection of parameterized key values Configlets can reference. For example, instead of hard-coding values such as NTP Servers or Syslog servers, you can define them in a Property Set.

> **NOTES**:
> 1. Passwords and other secret keys are not encrypted in Configlets.
> 2. You can use the same Configlets across the entire enterprise, but it’s a good idea to create regionally specific Property Sets.
> 3. Avoid using shortened versions of commands. 