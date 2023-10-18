# Exercise 1 - Adding a source system in the Identity Provisioning service

In this exercise, we will learn about the different types of systems in Identity Provisioning and we will configure a source system. 

The Identity Provisioning service ensures the synchronization of the entities between a source system and one or multiple target systems.

**Source Systems** 

A source system is the connector used for reading entities (users, groups, roles). Source systems can be on-premise or cloud-based, SAP or non-SAP, and usually represent the corporate user store where identities are currently maintained. Identity Provisioning reads the entities from the source system and creates or updates them in the relevant target ones. The provisioning is triggered from the Jobs tab of a source system.

You can connect one source system to one or multiple target systems.

<img src="/exercises/ex1/images/sourcesys.png" width=50% height=50%>

**Target Systems** 

A target system is the connector used for writing (provisioning) entities. Target systems are usually clouds, where Identity Provisioning creates or updates the entities taken from the source system.

A target system can be connected to a single or multiple source systems.

**Proxy Systems** 

A proxy system is a special connector used for "hybrid" scenarios. It exposes any Identity Provisioning supported backend system as a SCIM 2.0 service provider, which can be consumed by any SCIM 2.0Information published on non-SAP site compatible client application, without making a direct connection between them.

<img src="/exercises/ex1/images/proxy.png" width=50% height=50%>

More about it, on our product page under [System Types](https://help.sap.com/docs/identity-provisioning/identity-provisioning/system-types?locale=en-US).

The Identity Provisioning service supports provisioning of users and groups between multiple supported cloud and on-premise systems, both SAP and non-SAP. The complete list can be found under [Supported Systems](https://help.sap.com/docs/identity-provisioning/identity-provisioning/supported-systems?locale=en-US)


## Exercise 1.1 Creating a source system in IPS 

1. Navigate to the Identity Provisioning tab in the administrative console: 

<img src="/exercises/ex1/images/2IPS.png" width=50% height=50%>

2. Choose **Source Systems** from the drop-down list

<img src="/exercises/ex1/images/sources.png" width=50% height=50%>
 
3. In order to add a new Source Systenm, please press on **+Add**

<img src="/exercises/ex1/images/adds.png" width=50% height=50%>
   
4. Search for the **SAP SuccessFactors** connector Type

<img src="/exercises/ex1/images/choosesfsf.png" width=50% height=50%>
   
6. Choose a meaningfull name and description, such as **SAP SFSF**  and **my source system** for your system. Do not save yet the system.

<img src="/exercises/ex1/images/adddesc.png" width=50% height=50%>
   
8. Navigate to the third tab called **Properties** press on the button **Add** and choose **Standard**

<img src="/exercises/ex1/images/adddesc.png" width=50% height=50%>

10. For **Name** choose _sf.api.version_ and for **Value** write  _2_

<img src="/exercises/ex1/images/SFSF21.png" width=50% height=50%>
     
12.  When you are done press  **Save**.

 <img src="/exercises/ex1/images/SFSF2.png" width=50% height=50%>

14. Your saved system should look like this :
    
<img src="/exercises/ex1/images/SFSF3.png" width=50% height=50%>

15. After we have created the source system let us continue adding the rest of the necesary properties: 
The following properties are of type **Standard**

| Name         |Value | 
|--------------|:-----:|
| Authentication|BasicAuthentication|        
| ProxyType|Internet|   
| sf.user.attributes|userId,username,status,email,lastName,firstName,lastModifiedDateTime,personKeyNav|   
| sf.user.attributes.expand|personKeyNav,personKeyNav/userAccountNav|   
| Type|HTTP|   
|URL |https://apisalesdemo2.successfactors.eu/|   
|User | **Ask your supervisor**|  

The following property is of type **Credential**
| Name         |Value | 
|--------------|:-----:|
|Password | **Ask your supervisor**|   

16. Modify the following properties

| Name         |Value | 
|--------------|:-----:|
|ips.trace.failed.entity.content |true|  
|sf.user.filter |active eq "true"|  
16. Check that your properties are simmilar to the bellow screenshot and press  **Save**.

<img src="/exercises/ex1/images/pS3.png" width=50% height=50%>


## Summary

You've now created a source system for your SAP SuccessFactors instance. 

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

