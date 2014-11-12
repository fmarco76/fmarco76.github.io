---
layout: post
title:  OpenStack Summit 2014 in Paris - Report 
date:   2014-11-12 15:30:00
tags:
- OpenStack
---

During the [OpenStack summit in
Paris](https://www.openstack.org/summit/openstack-paris-summit-2014/){:target="_blank"}
I was interested to talks about federation and security. The following list includes
all the joined talks with some notes for each.


#### Barbican - Secrete Store

Barbican can write in different store using specific driver. The
Secrete Store is one of them.

Method in Barbican return the keys as private metadata (generally id
to retrieve the key)

HSM plugin perform encrypt/decrypt (very similar to the secrete store)

Barbican store encrypted secrets, if a secret is provided to Barbican
it retrieve a Key for the project and this is used to retrieve the keys
used to encrypt/decrypt the secret. The last step is performed by the
plug-in.

Dogtag plug-in is the upstream of RedHat Certificate Server

Goals for Kilo: multiple plug-in at a time, management of multiple CAs


#### Ephemeral PKI - SSL everywhere

The data path among OpenStack service is too complicate to be
protected at network level. Protect connection with TLS is the only
way but CRL and other protocol are not well supported in python
library used in OpenStack.

The approach used by HP is Ephemeral CA (use short life certificate).
This is available and it is possible to deploy (even in devstack) for test.


#### Using container without risk - user namespace

From kernel 3.10 user namespace are supported. This allows to create container with normal user privileges.

The risk becomes similar to a normal multi user linux machine.

Processes in a container are mapped with special id not corresponding
to users in the host so escalation from container to host is less
problematic.



#### Application and Network orchestration - Heat and Tosca

Just showed how heat and tosca work together to create an infrastructure (Heat) and run an application 
with all the related components (Tosca)


#### Identifying security issues - Analysis and best practice

Description of the STRIDE model.

Every vulnerability is evaluated with the DREAD system.

Some example of vulnerability and value shown. Ex. XEN XSA allows to
break the hypervisor (Amazon and Rackspace updated and rebooted their
infrastructure)



#### Keystone secure deploy - Best practices

A domain is create for admin purpose.

The default policy is wrong. It is better to use policy.v3cloudsample.json. Actually, it is not used
as default because of compatibility reason.



#### Barbican Hands-on - Keep secrets in OpenStack


Barbican provides a set of api to store and retrieve any information securely. This can be any kind of file.
If combined with HSM it can be a sort of secure storage. Not clear if it possible to do with swift.


#### PaaS and OpenStack - Agile Enterprise

PaaS is nice but requires to change many thinks. However, the talk did not explain too much,
just show some decision made to create a PaaS. Nothing relevant to us.


#### Docker meets Swift (this is made by RAI Television and IBM)

They are able to run code inside swift container to perform elaboration near data.

It require a private docker registry and another software, the Swift Storelet Manager,
which deploy the storelet (the application to run) from the registry to the container.

The storelet is an isolated container and the file endpoint is
provided by the manager so only the operation decided and the
specified file can be accessed.

There is a docker container running the storelet per operation per account.
The approach is similar to Zero VM but it is more flexible although it could be less secure.
It is not open source for now.




#### Tuning OpenStack - performance and availability in large deploy

Always hardware load balancer. Management in separate machine from the controller.
LDAP is good for user account but has to use the secure channel.

PKI tokens are better then UUID.

Many customisations for nova and KVM shown, better to check the slides
for tuning. The same for database and RabbitMQ


#### Cloud Security - Know the boundaries of your stack


The problem is to limit the VM in specific zones because data cannot
go to public cloud or does not comply with rules in other clouds.

Intel TXT is an hardware solution integrated in some processor and TPM
module providing integrity assurance of the boot process and the
remaining software stack.

To enable the Boundary control a GEO/ASSET Tag is added to the TPM (it
is signed and so on) and this is recognised by the bare metal and/or
hypervisors.
This is applicable to cinder volume also. 

Scripts and changes in OpenStack available for Juno


Another use case supported is the tenant control with encrypt and
decrypt of VMs. This make use of Barbican (an extension manage policy
has been created).  The private key for decrypt is in the TPM so only
the computer nodes with the key to decrypt can run the VM.

A blueprint for this approach has been proposed for Kilo but it is not
sure if it will be integrated or moved to a future version


#### Keystone to Keystone - Federation

The is to support federation-in (this is the normal identity
federation) and the federation-out (more similar to the idea of cloud
federation). The keystone-to-keystone makes use of SAML for the
communication. It require to configure the keystone to work as an IdP.



#### Cloud Federation - Are we there?

Points about the opportunity of federation almost in line with London article.
Investigation on how to create heat template spanning in federated clouds.
They mix the identity federation with the cloud federation!!!                                                                                
