# Exercise 4 - Identity Provisioning Operations - Manage Transformations

In this exercise, we will learn about the various Operations available in the Identity Provisioing service.

**Transformations**
For every system supported by the Identity Provisioning service, there is an initial (default) transformation logic that converts the system specific JSON representation of the entities from/to one common JSON. This default transformation is visible on the Transformations tab when you create a new system, after saving it. 

**Transformation Editors**
The Identity Provisioning service provides two editors for working with the transformation code: graphical editor and JSON (text) editor. The graphical editor is displayed by default. You can switch between them on the Transformations tab as we will see in the next exercise. 
Check the chapter [Transformations](https://help.sap.com/docs/identity-provisioning/identity-provisioning/transformations?locale=en-US) for more explanations and examples. 

## Exercise 4.1 Meet the graphical editor

Last executed job ran on an error. In this case, the reason was that the value for the department in the source system does not match the possible value in the target system. The scope of this exercise is to understand how to use the grphical editor, therefore we will perform a mapping between the possible values of the department attribute.  

1. From your SCI admin console navigate to the third tab Target Systems. We want to perform the value mapping in the target system because these values are specific to the Identity Directory target system specific.
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

12. Navigate to the **Provisioning Jobs** (from the Identity Provisioning drop-down menu) and notice how the job was now successfull.
    
<img src="/exercises/ex4/images/412.png" width=50% height=50%>

13. Press on the job result and inspect what changed now. 

<img src="/exercises/ex4/images/413.png" width=50% height=50%>

## Exercise 4.2 Change a property in the source system

## Exercise 4.2 Change a mapping in the target system

## Exercise 4.2 Run the validation job

## Exercise 4.2 Run the Read Job and create the users

After completing these steps you will have created...

