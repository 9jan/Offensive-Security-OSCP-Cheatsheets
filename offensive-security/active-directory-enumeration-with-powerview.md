# PowerView: Active Directory Enumeration

This lab explores a couple of common cmdlets of Powerview that related to Active Directory/Domain enumeration.

## Get-NetDomain

Gets current user's domain:

![](../.gitbook/assets/powerview-getnetdomain.png)

## Get-NetForest

Get information about forest the current user's domain is in:

![](../.gitbook/assets/powerview-forestinfo.png)

## Get-NetForestDomain

Get all domains of the forest the current user is from:

![](../.gitbook/assets/powerview-forest-domains.png)

## Get-NetDomainController

Get info about the DC of the domain the current user belongs to:

![](../.gitbook/assets/powerview-getdc.png)

## Get-NetGroupMember

Get a list of domain members that belong to a given group:

![](../.gitbook/assets/powerview-groups.png)

## Get-NetLoggedon

Get users that are logged on to a given computer:

![](../.gitbook/assets/powerview-connected-users.png)

## Get-NetDomainTrust

Enumerate domain trust relationships of the current user's domain:

![](../.gitbook/assets/powerview-domain-trusts.png)

## Get-NetForestTrust

Enumerate forest trusts fromt the current domain's perspective:

![](../.gitbook/assets/powerview-foresttrusts.png)

## Invoke-MapDomainTrust

Enumerate and map all domain trusts:

![](../.gitbook/assets/powerview-all-domain-trusts.png)

## Invoke-ShareFinder

Enumerate shares on a given PC - could be easily combines with other scripts to enumerate all machines in the domain:

![](../.gitbook/assets/powerview-enumerate-shares.png)

## Invoke-UserHunter

Find machines on a domain or users on a given machine that are logged on:

![](../.gitbook/assets/powerview-invoke-user-hunter.png)

{% embed url="https://github.com/PowerShellMafia/PowerSploit" %}

