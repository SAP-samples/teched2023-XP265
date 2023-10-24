# Exercise 2 - Adding a target system

In this exercise, you will create a target system for the source system created at the previous Exercise. 

## Exercise 2.1 Defining the Identity Directory as a target system

As we have learned in the [Getting started](../ex0/README.md) chapter, each SAP SCI tenant includes an Identity Directory  (IdDS) that stores user, groups and group assignments. In this exercise you will configure IdDS as a provisioning target.  

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab **Identity Provisioning** please choose **Target Systems**

<img src="/exercises/ex2/images/21.png" width=50% height=50%>

2. In order to add a new Target System, please press on **+Add**

<img src="/exercises/ex2/images/22.png" width=50% height=50%>
   
3. Search for the **Local Identity Directory** connector **Type**

<img src="/exercises/ex2/images/23.png" width=50% height=50%>  

4. Choose a meaningful name and description, such as **Local Identity Directory**  and **my local identity directory** for your system. Please be informed that the System Name cannot be changed once the system is saved
   
5. Under **Source Systems** you need to choose the source system that was created in the previous exercise

<img src="/exercises/ex2/images/25.png" width=50% height=50%>  

6. **Save** your system. Now your target system is created and it should look like this: 

<img src="/exercises/ex2/images/24.png" width=50% height=50%>


## Summary

You've now defined the IdDs of your SCI tenant as a provisioning target system for your scenario. 

Continue to - [Exercise 3 - Identity Provisioning Job Types](../ex3/README.md)
