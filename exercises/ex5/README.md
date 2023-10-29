# Exercise 5 - Advanced Identity Provisioning Operations

## Exercise 5.1 Editing Conditions 

1. Let's continue changing the default transformation by editing a condition in the source system. From your SCI admin console navigate to the third tab **Identity Provisioining** and choose **Source Systems**.
   
2. Choose the **SAP SFSF** source system  and navigate to the second tab **Transformations**.
   
3. Press on the **Edit** button from the right side of the menu.

4. Choose Edit Entity -> user -> Add condition.
   
<img src="/exercises/ex5/images/511.png">

6. In the pop-up copy the bellow conditions and press **Save**.

```
isValidEmail($.emails[0].value) && $.emails[0].value =~ /.*@successfactors.de/ 
```
<img src="/exercises/ex5/images/521.png">

This condition ensures that only users with a valid email address are read from the source system. Furthermore, the job will only filter for users with email addresses belonging to specific domains, in this case we want to only filter users that belong to a _SuccessFactors_ domain.

## Exercise 5.2 Meet the Simulate job

1. Navigate now to **Jobs**, the last tab of this source system
   
2. Choose **Simulate Job** and press on **Run Now**

<img src="/exercises/ex5/images/522.png">
   
3. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice the job result
   
4. At this stage many users would be deleted
<img src="/exercises/ex5/images/523.png">

6. You can check more information about this job execution. As these users are skipped because they don't fulfill the filtering criteria, press on **Download All Skipped Entity Logs for This job** from the top right corner: 

<img src="/exercises/ex5/images/526.png">

7. In the downloaded file you will see the following message:
   
<img src="/exercises/ex5/images/524.png">

In the next exercise you will learn how to use properties.

## Exercise 5.3 Working with Properties

You have already used properties to configure the connection between your source and target systems in the first exercise. However, this is not the only benefit one has from them. Properties help you to customize the way your identities are read from a source system or provisioned to the target one. They can also filter the entities and attributes which should be read or skipped during the provisioning job. 

1. Let's continue with the configuration from the previous exercise. Navigate to the **SAP SFSF** source system and go to the tab **Properties**. Add the following two **Standard** properties:

| Name         |Value | 
|--------------|:-----:|
|ips.trace.skipped.entity |true|  
|ips.trace.skipped.entity.content |true|  

The result should look like this: 

<img src="/exercises/ex5/images/531.png">

Press on **Save**. 

2. Navigate to the Target System **Local Identity Directory** and go the **Properties** tab

3. Modify the following property

| Name         |Value | 
|--------------|:-----:|
|ips.trace.failed.entity.content |true|  


If a provisioning job repeatedly fails and you need problem investigation, you can enable logging and tracing for the personal and sensitive data of your provisioned entities. To do this, set this property to true.

If the property is not set, in the logs you see: content = hidden content


4. Let us run the Simulate job one more time to see the result of our changes. For this we will navigate back to our source systems  and go to the last tab **Jobs**. Choose **Simulate Job** and press on **Run Now**
   
5. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu), notice the job result and download the skipped entities file.
   
<img src="/exercises/ex5/images/534.png">

Now you can notice that the domain used in the condition was wrong and therefore all the users will have been deleted, including the ones belonging to _*@successfactors.com_. This will be corrected in the next exercise. 

6. Return to the  **SAP SFSF** source system  and navigate to the second tab **Transformations**. Press on the **Edit** button from the right side of the menu. Choose Edit Entity -> user -> Edit condition.  Correct the existing condition as depicted bellow : 
   
```
isValidEmail($.emails[0].value) && $.emails[0].value =~ /.*@successfactors.com/ 
```
The result should look like this:

<img src="/exercises/ex5/images/536.png">

7. Press on **Save**.
   
8. Now that you have corrected the domain, simmulate the job one last time.  Navigate to the last tab **Jobs**. Choose **Simulate Job** and press on **Run Now**
   
9. As expected, not all read entities will be deleted. After checking the logs, you will notice that there are no more users with the  _*@successfactors.com_  domain skipped. The users that would be deleted are the ones belonging to other domains.

<img src="/exercises/ex5/images/539.png">
    
10.  Navigate to the **SAP SFSF* source system, choose the last tab **Jobs** and this time choose **Read Job** and press on **Run Now**
    
11.   Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice the job result.

<img src="/exercises/ex5/images/5311.png"> 

The expected ammount of users was deleted. 

These are just few of the many properties that you can use in IPS. All the available properties of the Identity Provisioning service can be found on our product page under [List of Properties](https://help.sap.com/docs/identity-provisioning/identity-provisioning/list-of-properties?locale=en-US&version=Cloud).

For example, in case one wants to limit the number of users deleted in the target system, the property `ips.delete.threshold.users` can be used. If more users than the value of the property should be deleted, then the job execution will be errored out, preventing the actual deletion. 

## Summary 
In this hands-on session you learned what the SAP Cloud Identity Services are and how to configure and troubleshoot systems in the Identity Provisioning service. 
