# Stable Configlets
Examples that have past rigorous QA without any known serious issues reported. Still requires modifying to match your precise deployment.

For more detailed information refer to [Configlet READ.md](../README.md)


# Stable Examples
Configlet examples in `payloads` are in JSON format. 

---

| Configlet | OS  | Use |
| --------- | --- | --- |
| x         | x   | x   |


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
