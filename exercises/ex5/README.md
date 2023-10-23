## Exercise 5.1 Editing Conditions 

1. Let's continue changing the default transformation by editing a condition in the source system. From your SCI admin console navigate to the third tab **Identity Provisioining** and choose **Source Systems**.
   
2. Choose the **SAP SFSF** source system  and navigate to the second tab **Transformations**.
   
3. Press on the **Edit** button from the right side of the menu.

4. Choose Edit Entity -> user -> Edit condition.
   
<img src="/exercises/ex5/images/511.png">

6. In the pop-up copy the bellow conditions and press **Save**.

<img src="/exercises/ex5/images/521.png">

```
isValidEmail($.emails[0].value) && (($.emails[0].value =~ /.*@successfactors.com/ ) || ($.emails[0].value =~ /.*@sap-test.de/ ))
```

This condition ensures that only users with a valid e-mail address are read from the source system. Furthermore, the job will only filter for users with email addresses belonging to specific domains. 

## Exercise 5.2 Meet the Simulate job

1. Navigate now to **Jobs**, the last tab of this source system.
   
2. Choose **Simulate Job** and press on **Run Now**

<img src="/exercises/ex5/images/522.png">
   
3. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice the job result.
   
4. We notice that many user would be deleted.

<img src="/exercises/ex5/images/523.png">

6. Let us try to see why. Press on **Download All Skipped Entity Logs for This job**

7. In the downloaded file we will see the following message :
   
<img src="/exercises/ex5/images/524.png">

In the next exercise we will learn how to use properties.

## Exercise 5.3 Working with Properties

We have already used properties to configure the connection between your source and target systems in the first exercises. However, this is not the only benefit we have from them. Properties help you to customize the way your identities are read from a source system or provisioned to the target one. They can also filter which entities and attributes to be read or skipped during the provisioning job. 

All the available properties to use in the Identity Provisioning service are to be found on our product page under [List of Properties](https://help.sap.com/docs/identity-provisioning/identity-provisioning/list-of-properties?locale=en-US&version=Cloud)).

1. Let us continue with the configuration from the previous exercise. Navigate to the **SAP SFSF** source system and go to the tab **Properties**. Add the following two properties:

| Name         |Value | 
|--------------|:-----:|
|ips.trace.skipped.entity |true|  
|ips.trace.skipped.entity.content |true|  

<img src="/exercises/ex5/images/531.png">

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
   
<img src="/exercises/ex5/images/532.png">

As expected no users would be deleted and the job is errored out - due to the _ips.delete.threshold.users_ property. Additionally to the previous job execution we can download both job logs for more details. 

This concludes our session today. If you want to exercise more with the SAP Cloud Identity Services but you do not have an environment already, check the trial account offerings as described in [Getting a Trial Tenant](https://help.sap.com/docs/identity-provisioning/identity-provisioning/getting-trial-tenant?locale=en-US&version=Cloud&q=trial%20account).


## Summary 
After completing this hands-on session you have learned whar are the SAP Cloud Identity Services and how to configure and troubleshoot systems in the Identity Provisioning service. 
