# keystone

*Dr Marco Fargetta*, INFN Catania

<span style="font-size:60%">marco.fargetta@ct.infn.it</span>

<span style="font-size:40%">CHAIN-REDS School on Cloud Computing. Catania, 13-18 April 2015</span>



## The identity management

- Keystone is the responsible for the identities inside OpenStack

- It grants the authorisation to the users before they can perform any operation

- Services need to communicate with Keystone


![OpenStack conceptual architecture](images/openstack_havana_conceptual_arch.png)




## User information

- **User**: represents a human user. Has associated information such as user name, password, and email

- **Group**: represents a collection of users. Roles can be assigned to groups and these are applied to all members

- **Project**: a context for users, roles and resources. For example, if you query the Compute service for a list of running instances, you get a list of all running instances in the project that you specified in your query

- **Domain**: defines administrative boundaries for the management of Identity entities



## Role and Policies

**Role** captures the operations that a user can perform. They have no
  special meaning inside Keystone but the services have to map each
  role with a specific action.

The mapping is done in a `policy.json` file like this

```javascript
{
    "admin_or_owner": [
        [
            "role:admin"
        ],
        [
            "project_id:%(project_id)s"
        ]
    ],
    "default": [
        [
            "rule:admin_or_owner"
        ]
    ],
    "compute:create": [
        "role:compute-user"
    ],
    "compute:create:attach_network": [
        "role:compute-user"
    ],
    "compute:create:attach_volume": [
        "role:compute-user"
    ],
    "compute_extension:admin_actions:pause": [
        [
            "rule:admin_or_owner"
        ]
    ],
    ....
```



## Service Catalog

- Keystone maintain the list of services available in the cloud

- This is used by users and services to get the service entry points

- It is possible to organise entry points in regions



## Modular architecture

- Default installation require a *MySql* database to store identity and other information

- Back-end module are divided in identity and assignments
    - *Identity* stores users and groups
    - *Assignment* stores domains, projects, roles and role assignment 

- Identity information can be maintained in a external server
    - LDAP and Active Directory can be associated to Keystone 



## User Authentication

- Default authentication based on **_username_** and **_password_**

- Credentials maintained in a database or retrieved from a corporate directory service
