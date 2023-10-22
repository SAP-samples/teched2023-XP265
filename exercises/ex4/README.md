# Exercise 4 - Identity Provisioning Operations

In this exercise, we will learn about the various Operations available in the Identity Provisioing service. We will start by understanding what are the transformations. 

**Transformations**
For every system supported by the Identity Provisioning service, there is an initial (default) transformation logic that converts the system specific JSON representation of the entities from/to one common JSON. This default transformation is visible on the Transformations tab when you create a new system, after saving it. 

**Transformation Editors**
The Identity Provisioning service provides two editors for working with the transformation code: graphical editor and JSON (text) editor. The graphical editor is displayed by default. You can switch between them on the Transformations tab as we will see in the next exercise. 
Check the chapter [Transformations](https://help.sap.com/docs/identity-provisioning/identity-provisioning/transformations?locale=en-US) for more explanations and examples. 

## Exercise 4.1 Meet the graphical editor

Last executed job ran on an error. In this case, the reason was that the value for the department in the source system does not match the possible value in the target system. The scope of this exercise is to understand how to use the grphical editor, therefore we will perform a mapping between the possible values of the department attribute.  

1. From your SCI admin console navigate to the third tab **Identity Provisioning** and choose Target Systems. We want to perform the value mapping in the target system because these values are specific to the Identity Directory target system specific.
In the **Local Identity Directory** target system that we created in Exercise 2, navigate to the second tab **Transformations**

<img src="/exercises/ex4/images/41.png" width=50% height=50%>

2. Notice the buttons on the upper right corner. From here you can shift between the two editors. Press on the button **Edit** and follow the next steps.

<img src="/exercises/ex4/images/42.png" width=50% height=50%>

3. The first entity is the **User**. Scroll down for the _Department_ attribute and press on the **Pencil** icon to Edit the maping.

<img src="/exercises/ex4/images/43.png" width=50% height=50%>

4. On the lower part of the pop-up menu, press on **Add** to  Add name-value pair for the specified expression. 

<img src="/exercises/ex4/images/44.png" width=50% height=50%>

5. Under Name choose **type**

<img src="/exercises/ex4/images/45.png" width=50% height=50%>

6. Under Value choose **valueMapping** and then **Save**

<img src="/exercises/ex4/images/46.png" width=50% height=50%>

7. To **Add a value mapping** choose the fifth button from top to bottom as displayed bellow.
   
<img src="/exercises/ex4/images/47.png" width=50% height=50%>

8. Press on **Add** to insert the new value.

<img src="/exercises/ex4/images/48.png" width=50% height=50%>

9. On the left collumn we will have the values from SAP SuccessFactors source system and on the right collumn the ones from the local Identity Directory. Please right the values as seen bellow and press on **Save**.
 
<img src="/exercises/ex4/images/49.png" width=50% height=50%>

10. You will see the changed also in the JSON editor. Simply shift the view and search for the rows 155 to 175.

<img src="/exercises/ex4/images/410.png" width=50% height=50%>

11. Now let us run the job again. Navigate to the Source System and choose the **SAP SFSF** source sytem. Press on the last tab **Jobs** and choose **Run Now**

<img src="/exercises/ex4/images/411.png" width=50% height=50%>

12. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice how the job was now successfull.
    
<img src="/exercises/ex4/images/412.png" width=50% height=50%>

13. Press on the job result and inspect what changed now. 

<img src="/exercises/ex4/images/413.png" width=50% height=50%>

14. Let us check a user record. From the SCI admin console navigate to the second tab **User Management**.

<img src="/exercises/ex4/images/414.png" width=50% height=50%>

15. We can search for the user "HR" because we remember that this was one of the users that had as department value _SMB_ in SAP SFSF - and this caused an error previously. Choose this user and let us scroll to the Department attribute.

<img src="/exercises/ex4/images/415.png" width=50% height=50%>

16. We can observe that the change in the mapping transfomration worked.

<img src="/exercises/ex4/images/416.png" width=50% height=50%>

## Exercise 4.2 Editing Conditions 

1. Let's continue changing the default transformation by editing a condition in the source system. From your SCI admin console navigate to the third tab **Identity Provisioining** and choose **Source Systems**.
   
2. Choose the **SAP SFSF** source system  and navigate to the second tab **Transformations**.
   
3. Press on the **Edit** button from the right side of the menu.

4. Choose Edit Entity -> user -> Edit condition.
   
<img src="/exercises/ex4/images/417.png" width=50% height=50%>

6. In the pop-up copy the bellow conditions and press **Save**.

```
isValidEmail($.emails[0].value) && (($.emails[0].value =~ /.*@successfactors.com/ ) || ($.emails[0].value =~ /.*@sap-test.de/ ))
```

This condition ensures that only users with a valid e-mail address are read from the source system. Furthermore, the job will only filter for users with email addresses belonging to specific domains. 

## Exercise 4.3 Meet the Simulate job

1. Navigate now to **Jobs**, the last tab of this source system.
   
2. Choose **Simulate Job** and press on **Run Now**
   
<img src="/exercises/ex4/images/418.png" width=50% height=50%>
   
3. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice the job result.
   
<img src="/exercises/ex4/images/419.png" width=50% height=50%>

4. We notice that many user would be deleted.

<img src="/exercises/ex4/images/420.png" width=50% height=50%>

6. Let us try to see why. Press on **Download All Skipped Entity Logs for This job**

7. In the downloaded file we will see the following message :
   
<img src="/exercises/ex4/images/421.png" width=50% height=50%>

In the next exercise we will learn how to use properties.

## Exercise 4.4 Working with Properties

We have already used properties to configure the connection between your source and target systems in the first exercises. However, this is not the only benefit we have from them. Properties help you to customize the way your identities are read from a source system or provisioned to the target one. They can also filter which entities and attributes to be read or skipped during the provisioning job. 

All the available properties to use in the Identity Provisioning service are to be found on our product page under [List of Properties](https://help.sap.com/docs/identity-provisioning/identity-provisioning/list-of-properties?locale=en-US&version=Cloud)).

1. Let us continue with the configuration from the previous exercise. Navigate to the **SAP SFSF** source system and go to the tab **Properties**. Add the following two properties:

| Name         |Value | 
|--------------|:-----:|
|ips.trace.skipped.entity |true|  
|ips.trace.skipped.entity.content |true|  

<img src="/exercises/ex4/images/423.png" width=50% height=50%>

Press on **Save**. 

2. Navigate to the Target System **Local Identity Services** and go the **Properties** tab.
3. We will add the property

| Name         |Value | 
|--------------|:-----:|
|ips.delete.threshold.users |2|  

the purpose of this property is to limit the number of users that are deleted in the target system. 

We will modify the following property

| Name         |Value | 
|--------------|:-----:|
|ips.trace.failed.entity.content |true|  

Note that these changes are solely for exercise purpose and in a real landscape you might have different requirements. 

4. Let us run the Simmulate job one more time to see the result of our changes. For this we will navigate back to our source systems  and go to the last tab **Jobs**. Choose **Simulate Job** and press on **Run Now**
   
4. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice the job result.
   
<img src="/exercises/ex4/images/425.png" width=50% height=50%>

Only two users would be deleted and the job is errored out. Additionally to the previous job execution we can download boad job logs for more details. 

This concludes our session today. If you want to exercise more with the SAP Cloud Identity Services but you do not have an environment already, check the trial account offerings as described in [Getting a Trial Tenant](https://help.sap.com/docs/identity-provisioning/identity-provisioning/getting-trial-tenant?locale=en-US&version=Cloud&q=trial%20account).


## Summary 
After completing this hands-on session you have learned whar are the SAP Cloud Identity Services and how to configure and troubleshoot systems in the Identity Provisioning service. 

