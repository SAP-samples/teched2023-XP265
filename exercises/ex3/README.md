# Exercise 3 - Identity Provisioning Operations - Job Types

In this exercise, we will learn about the various Operations available in the Identity Provisioing service and we will look in detail at the various provisioing job types available.  


## Exercise 3.1 Job types
You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.

The Identity Provisioning service provides the following types of provisioning jobs:
**Read Job**
Reads all entities from the source system and provisions only new or updated entities to the target system. If the job is run in delta read mode, it reads and provisions only new or updated entities in the source system.

**Resync Job** 
Reads all entities from the source system and provisions all entities to the target system.

**Simulate Job**
Estimates the number of entities that will be created, updated, deleted or skipped in the target system. Provides the expected results of a resync job without modifying the target system.

**Validate Job**
Verifies how entities (users and groups) would be mapped from source to target systems without modifying them.

If you want to know more about this, have a look at our product page under [Start and Stop Provisioning Jobs](https://help.sap.com/docs/identity-provisioning/identity-provisioning/start-and-stop-provisioning-jobs?locale=en-US&version=Cloud).


## Exercise 3.2 The Validate job

As previously mentioned in order to understand how IPS performs the mapping between source and target system, we can laverage the **Validate** Job.
Like the simulate job, the validate job predicts results in the target system without modifying it. However, unlike the simulate job (which estimates the number of entities that will be created, updated, deleted or skipped), the validate job verifies the content of the entities. 

To run a validate job, you need to import one or two CSV files - one for users and/or one for groups. Each file must contain a maximum of 10 users or groups with attributes as defined in the source system. The attribute names must use the JSONPath dot-notation. For example: emais[0].value attribute indicating the value of the first email within an email array, or name.familyName - a complex name attribute containing a familyName sub-attribute. If the file has more than 10 users or groups, the job will validate the first 10 and will ignore the rest.

You can create a CSV file using a text editor, for example Notepad. Make sure the number of fields match the number of headers in the file. Otherwise, you will get an error when importing the file and won't be able to proceed until you correct it.

For this exercise, we will use only a CSV file for users that was created for you. 

1. Download the prepared CSV file for users attached to this exercise.  The file is called **Users_SAPSFSF.csv**.

2. Navigate to the SCI administrative console that corresponds to your seat. From the third tab **Identity Provisioning** please choose **Source Systems**

<img src="/exercises/ex3/images/32.png" width=50% height=50%>

3. Choose the Source Sytsem created at Exercise 1 **SAP SFSF**


4. Once in the right system, navigate to the fifth Tab called **Jobs**

<img src="/exercises/ex3/images/34.png" width=50% height=50%>

   
5. Choose the last Job called **Validate** and press on **Run Now**. Choosing Run Now however does not trigger the job literally. It just opens a dialog box where you must import CSV (comma-separated values) files .

<img src="/exercises/ex3/images/35.png" width=50% height=50%>

   
6. In the Import Entities dialog box, browse for and select the CSV file that you downloaded earlier for testing users.

7. Press on **Validate**

<img src="/exercises/ex3/images/37.png" width=50% height=50%>

   
9. Your browser displayed a pop-up informing you that the results of the validate job are downloaded. Navigate to this folder locally on your computer and check the results.

<img src="/exercises/ex3/images/39.png" width=50% height=50%>



## Summary 
After completing these steps you will have learned how to master the Validate Job. 
