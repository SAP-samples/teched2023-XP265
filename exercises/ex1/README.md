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

## Exercise 1.1 Creating a source system in IPS 

1. Navigate to the Identity Provisioning tab in the administrative console: 

<img src="/exercises/ex1/images/2IPS.png" width=50% height=50%>

2. Choose **Source Systems** from the drop-down list

<img src="/exercises/ex1/images/sources.png" width=50% height=50%>
 
3. In order to add a new Source Systenm, please press on **+Add**
4. Search for the **SAP SuccessFactors** connector Type
5. Choose a meaningfull name and description for your system and when you are done press on **Save**


## Example 1.1 Sub Exercise 1 Description

After completing these steps you will have created...

1. Click here.
<br>![](/exercises/ex1/images/01_01_0010.png)

2.	Insert this line of code.
```abap
response->set_text( |Hello World! | ). 
```



## Example 1.2 Sub Exercise 2 Description

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex1/images/01_02_0010.png)


## Summary

You've now ...

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

