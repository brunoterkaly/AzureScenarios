<a name="Title"></a>
# Setting up an Azure Virtual Machine For Developers with Visual Studio 2013 Ultimate and SQL Server 2012 Express #

---
<a name="Overview"></a>
## Overview ##

This next section is about getting set up with Azure Virtual Machine that includes Visual Studio 2013 RC and SQL Server 2012 Express. This will be the starting point for other labs.

In this hands-on lab, you will explore the basic elements of setting up an **Windows Azure Virtual Machine** using the Windows Azure Gallery for Vitual Machines. Once a basic virtual machine has been setup, we will add SQL Server 2012 Express Edition.

<a name="Objectives"></a>
### Objectives ###

In this hands-on lab, you will learn how to:

- Create a Virtual Machine with Visual Studio 2013 RC from the Windows Azure Management Portal
- Download and install SQL Server 2012 Express

<a name="Prerequisites"></a>
### Prerequisites ###

The following is required to complete this hands-on lab:

- A Windows Azure subscription

<a name="Setup"></a>
### Setup ###

In order to execute the exercises in this hands-on lab you need to set up your environment.

1. Start by logging into the **Windows Azure Portal** (http://manage.windowsazure.com).


---
<a name="Exercises"></a>
## Exercises ##

This hands-on lab includes the following exercises:

- [Getting Started: Creating an Azure Virtual Machine using the Windows Azure Virtual Image Gallery](#GettingStarted)
- [Exercise 1: Downloading and installing SQL Server 2012 Express](#Exercise1)

<a name="GettingStarted"></a>
### Getting Started: Creating an MVC 4 Application using Entity Framework Code First ###

In this section, you will log into the Windows Azure Portal and create an Azure Virtual Machine using the Windows Azure Gallery. 

<a name="GettingStartedTask1"></a>
#### Task 1 – Creating an Azure Virtual Machine using the Windows Azure Virtual Image Gallery ####

1. Return back to the **Windows Azure Portal**. To start select **virtual machines** from the left menu panel. Next, click the **+New** button in the lower left corner. 

	![Creating a Windows Azure SQL Virtual Machine](Images/image001.jpg?raw=true)

	_Creating a Windows Azure SQL Virtual Machine_

1. Next, select **Virtual Machine | From Gallery** from the portal. You will then be provided a list of virtual machine images to choose from. We are interested in SQL Server 2012 Sp1. 

	![Choosing a base image from the gallery](Images/image002.jpg?raw=true)

	_Choosing a base image from the gallery_

1. Notice that there are many versions of SQL Server available on various operating systems. Make the selection as seen below, **SQL Server 2012 SP1 Enterprise on WS 2012**. 

	![Selecting SQL Server 2012 SP1 Enterprise on WS 2012](Images/image003.jpg?raw=true)

	_Selecting SQL Server 2012 SP1 Enterprise on WS 2012_

1. This next screen allows you to specify a **virtual machine name**. You will need to choose a unique name that is not already chosen. This screen also allows you to specify the **machine size**. For testing purposes we recommend a **small size** as there won’t be much load for an individual developer. You will also need to specify a **username** and **password** that will be used to log into the machine. This will not be the same username and password for the web application. We will need to add a database user separately using **SQL Server Mangement Studio** in a future step. 

	![Configuring the Virtual Machine](Images/image004.jpg?raw=true)

	_Configuring the Virtual Machine_

1. You will also need to provide a **DNS name**, which represents the unique name of the server on the web. It also specify a **Region**, we should generally be the same **Region** as the applications that will be consuming the database to minimize latency. 

	![Configuring the Virtual Machine](Images/image005.jpg?raw=true)

	_Configuring the Virtual Machine_

1. No changes or modifications are needed for this final step in the virtual machine configuration. 

	![Configuring the Virtual Machine](Images/image006.jpg?raw=true)

	_Configuring the Virtual Machine_

1. We are now ready to begin the importing of the **Bacpac** file that was created in Exercise 1. To accomplish this task, we will need to use **Remote Desktop** to connect to the **Virtual machine** directly. From there we will start **SQL Server 2012 Mangement Studio** to perform the actual import process. For this step, click the **Connect** option from the bottom menu bar. 

	![Importing into Windows Azure SQL Virtual Machine](Images/image007.jpg?raw=true)

	_Importing into Windows Azure SQL Virtual Machine_

1. A popup window will appear at the bottom of the browser window. Click on the **Open** button to start a remote desktop session. You will need to use the **Username** and **Password** specified when you created the **virtual machine** in the previous step. 

	![Opening a Remote Desktop Session](Images/image008.jpg?raw=true)

	_Opening a Remote Desktop Session_

1. You are now remotely connected to the virtual machine you just created. The next step is to start SQL Server 2012 Mangement Studio. 

	![Starting SQL Server 2012 Mangement Studio](Images/image009.jpg?raw=true)

	_Starting SQL Server 2012 Mangement Studio_

1. The **virtual machine** comes equipped with SQL Server 2012 Mangement Studio. Select from the **start menu** and launch it. 

	![Starting SQL Server 2012 Mangement Studio](Images/image010.jpg?raw=true)

	_Starting SQL Server 2012 Mangement Studio_

1. It may take a few moments to load the first time. 

	![Starting SQL Server 2012 Mangement Studio](Images/image011.jpg?raw=true)

	_Starting SQL Server 2012 Mangement Studio_

1. You will be presented with the appropriate default parameters to connect to the database server. You don't need to enter anything.  Just click the **connect** button. 

	![Connecting to dataase with Windows Authentication](Images/image012.jpg?raw=true)

	_Connecting to dataase with Windows Authentication_

1. We are now ready to import the data tier, which is really the **Bacpac** file that we had created earlier. As you recall, that file is sitting in **Windows Azure storage**. Right mouse click on **Databases** and select **Import Data Tier**. 

	![Importing a Data-tier Application](Images/image013.jpg?raw=true)

	_Importing a Data-tier Application_

1. The wizard will begin and you will be presented with various screens to import the database. Click **Next** on the **Import Data-tier Application Wizard**.  

	![Starting the import wizard](Images/image014.jpg?raw=true)

	_Starting the import wizard_

1. Because the **Bacpac** file is sitting in **Windows Azure storage**, select the **radio button |  Import from Windows Azure**. At this point you should click **Connect,** assuming you have the storage account information. If you do not, the next steps will allow you to get that information. If you have the **Storage Account Name** and the **Primary Access Key**, you can skip past the portal help section in the next 2 steps. 

	![Importing Data-tier Application](Images/image015.jpg?raw=true)

	_Importing Data-tier Application_

1. The point of this step is to verify that you have not forgotten the details of the **Bacpac** file inside of **Windows Azure Storage**. You can return back to the **Windows Azure portal** and click **Storage** on the left menu. You should be able to easily identify the **Bacpac** file that you had created previously in an earlier exercise. Once you highlight the **Bacpac** file, you can select **Manage access keys** from the bottom of the screen. The access key will be needed for the import process in **SQL Server Mangement Studio**. 

	![Importing Data-tier Application](Images/image016.jpg?raw=true)

	_Importing Data-tier Application_

1. As explained previously, you may need the **primary access key**. When at the portal, note that you can now access the primary access key and copy it to the clipboard so that it can be used for the import within **SQL Server Mangement Studio** in this step. Notice you need to provide the **Storage Account Name** as well as the **Account Key**. Enter that information then enter **Connect**. 

	![Importing Data-tier Application](Images/image017.jpg?raw=true)

	_Importing Data-tier Application_

1. You should be able to select the **Container** name from the drop down combo box. Click **Next** to continue. 

	![Importing Data-tier Application](Images/image018.jpg?raw=true)

	_Importing Data-tier Application_

1. You will also be able to select the **file name** for the **Bacpac** file. 

	![Importing Data-tier Application](Images/image019.jpg?raw=true)

	_Importing Data-tier Application_

1. Accept the default values and click the **Next** button. 

	![Importing Data-tier Application](Images/image020.jpg?raw=true)

	_Importing Data-tier Application_

1. The import process is now complete. Click **Finish** to dismiss the import data tier wizard. 

	![Importing Data-tier Application](Images/image021.jpg?raw=true)

	_Importing Data-tier Application_

1. Verify that your import a successful and click **Close**. 

	![Importing Data-tier Application](Images/image022.jpg?raw=true)

	_Importing Data-tier Application_

1. You can now verify that all the database structures, as well as the data is available. Right mouse click on the **Customers table** and create a select **Query** in a **New query editor window**. A simple query can verify if all the appropriate data structures and data are made it through the import process. 

	![Verifying the import with SQL Server Management Studio](Images/image023.jpg?raw=true)

	_Verifying the import with SQL Server Management Studio_

1. Execute the query and verify that the correct data appears in the results pane below. 

	![Verifying the import with SQL Server Management Studio](Images/image024.jpg?raw=true)

	_Verifying the import with SQL Server Management Studio_

1. Let’s begin by starting **SQL Server Configuration Manager**. 

	![Starting SQL Server Configuration Manager](Images/image025.jpg?raw=true)

	_Starting SQL Server Configuration Manager_

1. Once **SQL Server Configuration Manager** is open, navigate to the section on the left called **SQL Server network configuration | Protocols for MSSQLSERVER**. Be sure to enable **Named Pipes**. You can close **SQL Server Configuration Manager** now. 

	![Changing SQL Server Configuration Management](Images/image026.jpg?raw=true)

	_Changing SQL Server Configuration Management_

1. We now need to return back to the portal and open up TCP port 1433 the virtual machine. Start by selecting the **virtual machine** previously created, and click the **->** to the right of the virtual machine name (**DBMvcSample**). 

	![Opening up TCP Port 1433](Images/image027.jpg?raw=true)

	_Opening up TCP Port 1433_

1. From the top level menu select **Endpoints**, then click the **Add** button from the bottom of the portal window. 

	![Opening up TCP Port 1433](Images/image028.jpg?raw=true)

	_Opening up TCP Port 1433_

1. The dialog box is for you select the **Name, Protocol, the Public and Private ports**. Fill in the dialog box as seen below. As mentioned previously, for security purposes, it might make sense to use another lesser-known port then **1433**. 

	![Opening up TCP Port 1433](Images/image029.jpg?raw=true)

	_Opening up TCP Port 1433_

1. From the **Start** menu, choose **Windows Firewall with Advanced...**. 

	![Starting the Windows Firewall](Images/image030.jpg?raw=true)

	_Starting the Windows Firewall_

1. Right mouse click on **Inbound Rules** and choose **New Rule**. 

	![Adding an Inbound Rule](Images/image031.jpg?raw=true)

	_Adding an Inbound Rule_

1. The second radio button is **Port**, so select **Port** and click the **Next** button. 

	![Adding an Inbound Rule](Images/image032.jpg?raw=true)

	_Adding an Inbound Rule_

1. Be sure that the rule applies to **TCP** ports, specifically port **1433,** as seen below. 

	![Adding an Inbound Rule](Images/image033.jpg?raw=true)

	_Adding an Inbound Rule_

1. The action that we desire is to **Allow the Connection**. Then click **Next**. 

	![Adding an Inbound Rule](Images/image034.jpg?raw=true)

	_Adding an Inbound Rule_

1. By default all three checkboxes are enabled. Do not change them and click **Next**. 

	![Adding an Inbound Rule](Images/image035.jpg?raw=true)

	_Adding an Inbound Rule_

1. Provide a **Name** for the new **Inbound rule** that we just created and click **Finish**. You are now done configuring the Windows firewall to allow **Incoming TCP connections** on **Port 1433.** 

	![Adding an Inbound Rule](Images/image036.jpg?raw=true)

	_Adding an Inbound Rule_

1. We also want to use **SQL Server Authentication**, in addition to **Windoows Integrated Authentication**. 

	![In this next section we need to add a **New Login** so we can connect to the database using a connection string and not use the built-in **Administrator** account. ](Images/x?raw=true)

	_In this next section we need to add a **New Login** so we can connect to the database using a connection string and not use the built-in **Administrator** account. _

1. As previously stated, because our connection string will leverage SQL Server standard security, we will need to create a new login user that leverages **SQL Server Authentication**. Right mouse click **Security | Logins | New Login**. 

	![Adding a **New Login** and **SQL Server Authentication**](Images/image037.jpg?raw=true)

	_Adding a **New Login** and **SQL Server Authentication**_

1. Enter a login name and remember what you indicated. It will be needed in the connection string later from our web application. In this example we will call the login name **TestUser**. De-select **Enforce password policy**. 

	![Adding a **New Login** and **SQL Server Authentication**](Images/image038.jpg?raw=true)

	_Adding a **New Login** and **SQL Server Authentication**_

1. From the left side of the dialog box under **Select a Page**, click on **User Mapping**. Be sure to map **TestUser** to **MVC4Sample**. Make sure the **Default Schema** reads **db_owner**. Lower in the dialog box for **Database Role Membership**, select **db_owner** and **public**. 

	![Adding a **New Login** and **SQL Server Authentication**](Images/image039.jpg?raw=true)

	_Adding a **New Login** and **SQL Server Authentication**_

1. In the final step we will need to enable **SQL Server Authentication**. This can be done by choosing **properties** after right mouse clicking on **SQL Server** and the **object Explorer**, as seen below. 

	![Restarting SQL Server](Images/image040.jpg?raw=true)

	_Restarting SQL Server_

1. On the left side of the dialog box choose **Security** and be sure that under server authentication you have chosen**SQL Server and Windows authentication mode**. Click **OK** when finished. 

	![Modifying Server Properties](Images/image041.jpg?raw=true)

	_Modifying Server Properties_

1. In order for all these changes take effect, you will need to restart the database. Right mouse click on **SQL Server** and choose **Restart**. 

	![Restarting SQL Server](Images/image042.jpg?raw=true)

	_Restarting SQL Server_

1. Choose **Yes** from the pop-up dialog box to indicate that you do wish to restart the server. 

	![Verifying the restart](Images/image043.jpg?raw=true)

	_Verifying the restart_

1. Start Visual Studio 2013 Ultimate. From the **View** menu, choose **Server Explorer**. 

	![Starting Server Explorer in Visual Studio](Images/image044.jpg?raw=true)

	_Starting Server Explorer in Visual Studio_

1. Right mouse click on **Data Connection** in **Server Explorer** and choose **Add Connection** 

	![Adding a database connection](Images/image044.jpg?raw=true)

	_Adding a database connection_

1. Select **Microsoft SQL Server** and clilck **Continue**. 

	![Choosing the data source](Images/image045.jpg?raw=true)

	_Choosing the data source_

1. Type in the server name of the **Windows Azure SQL Virtual Machine** you created earlier. Yours will be different from **dbmvcsample.cloudapp.net**. Next select **Use SQL Server Authentication** and type in the **User name** and **Password**. Next, select **Selet or enter a database name** and you should be able to see **MVC4Sample**. Finally, click **Test Connection** to verify the database is available. 

	![Adding the connection](Images/image046.jpg?raw=true)

	_Adding the connection_

1. Right mouse click on **Tables | Customers** and select **New Query**. Next, type in **select * from Customers**. 

	![Creating a query](Images/image047.jpg?raw=true)

	_Creating a query_

