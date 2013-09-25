
<a name="Title"></a>
# Creating a Storage Account #

---
<a name="Overview"></a>
## Overview ##

A **storage account**  is needed to store the **bacpac** file. You will create the **bacpac** file, which represents a compressed format for your on-premises SQL Server database. 

It is a logical backup (**bacpac**) file containing the schema definition and table data. Windows Azure storage is needed to store this file. This **bacpac** will then be imported into our Windows Azure SQL virtual machine (IaaS) in a future lab. 

You will need to remember the **Storage Account Name** as well as the **Access** key so you can import the **bacpac** file.

### High Level Options ###

![High Level Diagram](Images/overview.png?raw=true "High Level Diagram")

_Windows Azure Storage and the **bacpac** file_

<a name="Objectives"></a>
### Objectives ###

In this hands-on lab, you will learn how to:

- Create a **Storage Account** so that you can store the **bacpac** file once it is exported

<a name="Prerequisites"></a>
### Prerequisites ###

The following is required to complete this hands-on lab:

- A Windows Azure subscription

> **Note:** This lab is required for a future labs where the export and import of the **bacpac** file takes place. You will import the **bacpac** file into **Windows Azure SQL Virtual Machine**.

<a name="Setup"></a>

### Setup ###

In order to execute the exercises in this hands-on lab you need to set up your environment.

1. Start by logging into the **Windows Azure Portal** (http://manage.windowsazure.com).


---
<a name="Exercises"></a>
## Exercises ##

This hands-on lab includes the following exercises:

- [Getting Started: Creating an **Windows Azure Storage Account**](#GettingStarted)

<a name="GettingStarted"></a>
### Getting Started: Creating an **Windows Azure Storage Account** ###

In this section, you will log into the Windows Azure Portal and create an **Windows Azure Storage Account**.

<a name="GettingStartedTask1"></a>
#### Task 1 – Getting Started: Creating an **Windows Azure Storage Account** ####

This lab plays an important role for 2 other labs. This lab is all about establishing a **Storage Account**. This **Storage Account** will be used to store a **bacpac** file. The **bacpac** file will be a compressed database file. We will create this file using an on premises SQL Server database.


1. Login into the **Windows Azure Portal**. On the left menu pane, select **Storage**. In the lower left corner select **+New** to create a new **Storage Account**. 

	![Creating a **Storage Account**](Images/Image001.jpg?raw=true)

	_Creating a **Storage Account**_

1. From the screen below, select **Storage | Quick Create**. 

	![Using Quick Create](Images/Image002.jpg?raw=true)

	_Using Quick Create_

1. Storage accounts are publicly exposed REST endpoints. This means that content can be accessed with ordinary http access. Note that in the screen below we need to provide the first segment of the **URL**. Notice that we choose **bacpackincloud**. You will need to choose your own **URL**. Naturally, files can also be made private, accessible with only a security key. Each **Storage Account** can contain one or more containers. Inside of each container is where files can be placed. These files are also known as **Blobs**. In the next exercise we will export the on-premises database as a **bacpac file** as a **blob,** inside a **container,** inside a **storage account**. In summary, you will provide 2 things here: (1) **URL**; (2) **Data Center Location**.  Finally, hit the **Create Storage Account** button on the lower right. 

	![Providing **Storage Account** Details](Images/Image003.jpg?raw=true)

	_Providing **Storage Account** Details_

1. It may take a few moments for the **Storage Account** to finish completion. 

	![Waiting for the **Storage Account** to complete](Images/Image004.jpg?raw=true)

	_Waiting for the **Storage Account** to complete_

1. At the bottom of the screen you will see a button called, **Manage Access Keys**. You will then be provided a popup dialog box where you can choose to copy the **management key** to the clipboard. You will need the **management key** for a future step, so you may want to copy it to a text file somewhere for future reference. After you've copied it, click the **checkmark** to dismiss the dialog box. 

	![Getting the **Management Access Keys (Primary Access Keys)**](Images/Image005.jpg?raw=true)

	_Getting the **Management Access Keys (Primary Access Keys)**_

1. Now that we've create a **Storage Account**, we have 2 vital pieces of information - the Account Storage Name and the Primary Access Key. You will need these pieces of data for future labs. 

<a name="Summary"></a>
## Summary ##
This lab laid the groundwork for you to upload a **bacpac** file, which will be used as a temporary or permanent storage location. The **bacpac** file will be used "re-hydrate" the on-premises database in **Windows Azure SQL Virtual Machine**	.
