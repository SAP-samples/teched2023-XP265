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

After completing these steps you will have created...
