---
title: Workflow - Tests
# tags:
#     - 
author: AlexHedley
# description: 
published: 2016-07-14
---

In this Article I will explain how to add Tests to your Workflow projects.
  
Everyone is running tests aren't they?
  
![Test In Production](images\TestInProduction.jpg)
  
We are going to create a simple WebService Project.
  
Create a new ![Decision Only](images\DecisionOnly.png) Decision Project.
  
Add a new ![Model 2](images\Model2.png) Model called **Test**.
  
Set an Input and Output

| Input | Param |
| --- | --- |

| Output | Success |
| --- | --- |

Add a simple Workflow that tests for a given param word. In this case my Name - "Alex"
  
![POC_DataService_DEC](images\POC_DataService_DEC.png)
  
Right-Click on the Model **Test** and "Set Model As Invocation Target".
  
Next Right-Click on the Project and select "New Test".
  
![RightClick Project](images\RightClickProject.png)
  
Give it a **Name** and choose your **Model**.
  
![New Test](images\NewTest.png)
  
Now fill in the required fields
  
General
  
![Test - General](images\Test-General.png)
  
Data
  
Click on the ellipse and fill in the param(s):
  
![Test - Data](images\Test-Data.png)
  
The Params are shown from the Parameters in the Model.
  
![Test Start Data](images\TestStartData.png)
  
Now fill in your condition to check in the End Data
  
![End Data](images\EndData.png)
  
Repeat for as many tests as you need, I just need the opposite so failed via a param that isn't "Alex".
  
Click Debug. ![Debug](images\Debug.png)
  
There will be a new line in under the usual options - "Test"
  
![Test - Debugging Form](images\Test-DebuggingForm.png)
  
Click **Run**
  
![Test - Run Tests](images\Test-RunTests.png)
  
They will then start "Running" or be "Pending".
  
![Test - Run Tests - Running Pending](images\Test-RunTests-RunningPending.png)
  
Then hopefully you should have them all Pass.
  
![Test - Run Tests - Passed](images\Test-RunTests-Passed.png)

[![Protirus](images\Protirus.png)](https://www.protirus.com/)
