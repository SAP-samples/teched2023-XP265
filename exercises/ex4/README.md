# Exercise 4 - Identity Provisioning Operations

In this exercise, we will learn about the various Operations available in the Identity Provisioing service. We will start by understanding what transformations are. 

**Transformations**
For every system supported by the Identity Provisioning service, there is an initial (default) transformation logic that converts the system specific JSON representation of the entities from/to one common JSON. This default transformation is visible on the Transformations tab when you create a new system, after saving it.

**Transformation Editors**
The Identity Provisioning service provides two editors for working with the transformation code: graphical editor and JSON (text) editor. The graphical editor is displayed by default. You can switch between them on the Transformations tab as we will see in the next exercise. 
Check the chapter [Transformations](https://help.sap.com/docs/identity-provisioning/identity-provisioning/transformations?locale=en-US) for more explanations and examples. 

## Exercise 4.1 Meet the graphical editor

In the previous exercise, an error occurred in the last executed job. In this case, the reason was that the value for the department in the source system does not match one of the possible values in the target system. The scope of this exercise is to understand how to use the graphical editor, therefore we will perform a mapping between the possible values of the `department` attribute.  

1. From your SCI admin console navigate to the third tab **Identity Provisioning** and choose Target Systems. We want to perform the value mapping in the target system because these values are specific to the Identity Directory target system specific.
In the **Local Identity Directory** target system that we created in Exercise 2, navigate to the second tab **Transformations**

<img src="/exercises/ex4/images/41.png">

2. Notice the buttons on the upper right corner. From here you can shift between the two editors. Press on the button **Edit** and follow the next steps

<img src="/exercises/ex4/images/42.png">

3. The first entity is the **User**. Scroll down for the `department` attribute and press on the **Pencil** icon to edit the mapping

<img src="/exercises/ex4/images/43.png">

4. On the lower part of the pop-up menu, press on **Add** to add name-value pair for the specified expression

<img src="/exercises/ex4/images/44.png">

5. Under Name choose **type**

<img src="/exercises/ex4/images/45.png">

6. Under Value choose **valueMapping** and then **Save**

<img src="/exercises/ex4/images/46.png">

7. To **Add a value mapping** choose the fifth button from top to bottom as displayed bellow
   
<img src="/exercises/ex4/images/47.png">

8. Press on **Add** to insert the new values in step 9

<img src="/exercises/ex4/images/48.png">

9. On the left column we will have the values from SAP SuccessFactors source system and on the right column the ones from the local Identity Directory. Please add the values as seen bellow and then press on **Save**
 
<img src="/exercises/ex4/images/49.png">

10. You will see the changes also in the JSON editor. Simply shift the view and search for the rows 155 to 175

<img src="/exercises/ex4/images/410.png">

11. Now let us run the job again. Navigate to the source system and choose the **SAP SFSF** source system. Press on the last tab **Jobs** and choose **Run Now** for the **Read Job**

<img src="/exercises/ex4/images/411.png">

12. Navigate to the **Provisioning Logs** (from the Identity Provisioning drop-down menu) and notice how the job was now successful
    
<img src="/exercises/ex4/images/412.png">

13. Press on the job result and inspect what changed now

<img src="/exercises/ex4/images/413.png">

14. Let us check a user record. From the SCI admin console navigate to the second tab **User Management**

<img src="/exercises/ex4/images/414.png">

15. We can search for the user "HR" because we remember that this was one of the users that had as `department` value `SMB` in SAP SFSF - and this caused an error previously. Choose this user and let us scroll to the `department` attribute

<img src="/exercises/ex4/images/415.png">

16. We can observe that the change in the mapping transformation worked

<img src="/exercises/ex4/images/416.png">


## Summary 
After completing these steps you learned what the transformations are and how they can be changed. We edited the value mapping for the attribute `department` and tested the results of our changes. Join us on the next exercise to learn more exciting IPS features [Exercise 5 - Advanced Identity Provisioning Operations](../ex5/README.md)

