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

1. On the left menu pane, select **SQL Databases**. You will see a list of existing databases. Toward the top you will see **Servers** as an option. Select **Servers**. 

	![Creating a server to host your Windows Azure SQL Database](Images/image001.png?raw=true)

	_Creating a server to host your Windows Azure SQL Database_

1. You will see a list of servers. You could simply get the name of an existing server or you can choose to click on the **Add** button on the lower menu bar. This will create an additional **server**. 

	![Creating a server to host your Windows Azure SQL Database](Images/image002.png?raw=true)

	_Creating a server to host your Windows Azure SQL Database_

1. Before the **Server** is actually created, you will need to indicte the **Login Name**, **Login Password**, and the **Region**. You can optionally indicate, **Allow Windows Azure Services to access the server** - if you want to expose the server through TCP/IP to other servers in a Microsoft data center. 

	![Specifying Login, and Region](Images/image003.png?raw=true)

	_Specifying Login, and Region_

1. The new **Server** should appear in the portal. The name of the **Server** is **s9d2fjlu9s**. The full name is **s9d2fjlu9s.database.windows.net**. 

	![Verifying server creation](Images/image004.png?raw=true)

	_Verifying server creation_

1. The name of the **Server** is **s9d2fjlu9s**. Take note of the **Server** name. It will be needed by **SQL Server Management Studio** during the migration process. 

	![Verifying server creation](Images/image005.png?raw=true)

	_Verifying server creation_

1. In this step you will be required to access the **Configure** menu near the top. It will allow you to enter a range of IP addresses that can have access to the server. One or more ranges can be added. Each range of IP addresses represents **allowed IP addresses** to access the server. This is a way to enforce some degree of security. It assumes that you know the potential IP addresses of clients connecting to your server. 

	![Selecting the Configure Menu](Images/image006.png?raw=true)

	_Selecting the Configure Menu_

1. Note that to keep this demo simple we **allowed all clients** to connect to the server **s9d2fjlu9s**. This is not a recommended practice.

	![Adding Allowed IP addresses](Images/image007.png?raw=true)

	_Adding Allowed IP addresses_

1. To be clear, this is not a recommended practice. Notice the rule name is **DoNotUse**. Notice the **allowed IP range** is **0.0.0.0 to 255.255.255.255**. 

	![Adding Allowed IP addresses](Images/image008.png?raw=true)

	_Adding Allowed IP addresses_

1. We will perform the migration to **Windows Azure SQL Database** from an on-premises database. But to do so, we need the **full address** of our **server** (the server for **Windows Azure SQL Database**). The name of the **Server** is **s9d2fjlu9s**. The full name is **s9d2fjlu9s.database.windows.net**. 

	![Getting the full server name](Images/image009.png?raw=true)

	_Getting the full server name_

1. Now that we have the **Server name**, we are ready to perform the migration using **SQL Server Management Studio**, which has the built-in tooling to perform the **migration process**. Login to your on-premises database server where you would like to do your migration **from**. 

	![Migrating the on-premises database](Images/image010.png?raw=true)

	_Migrating the on-premises database_

1. Right mouse click on **MVC4Sample** and choose **Tasks | Deploy Database to SQL Azure**. 

	![Migrating the on-premises database](Images/image011.png?raw=true)

	_Migrating the on-premises database_

1. The migration wizard needs to know the **Server name** you wish to target with the migration. In previous steps we've identified, the **full address** of our **server**. The full name is **s9d2fjlu9s.database.windows.net**. You **Server name** will be different. **Server names** are globally unique. Click the **Connect** button to the right of **Server connection** on the migration wizard. 

	![Migrating the on-premises database](Images/image012.png?raw=true)

	_Migrating the on-premises database_

1. You will now be asked for the **Server name, Login/Password**. Be sure to select **SQL Server Authentication**. You will need to recall all of this information duing the Windows Azure SQL Database Server creation process in earlier steps. 

	![Identifying the target database server in Windows Azure](Images/image013.png?raw=true)

	_Identifying the target database server in Windows Azure_

1. Once you've finished **Connecting** to the target server for the migration, you are ready to enter some more information, such as **New database name, the edition ofSQL Database (SQL Azure is the old name, btw), and the maximum database size (5 GB)**. Click **Next** when you have entered in this information. 

	![Deployment Settings](Images/image014.png?raw=true)

	_Deployment Settings_

1. You have now finished specifying the details for the migration to Windows Azure SQL Database. Click **Finish** to start the actual and physical migration. 

	![Viewing the summary information](Images/image015.png?raw=true)

	_Viewing the summary information_

1.  everything goes as planned, you will see the **Operation Complete** dialogbox with the **Result** being **Success** for all activities. Click **Close** to dismiss the migration wizard. 

	![Viewing the migration results](Images/image016.png?raw=true)

	_Viewing the migration results_

1. Return back to the Windows Azure Portal. Click on **SQL databases** on the left pane. The list of databases should include **MVC4Sample**. Next, click on the **Manage** menu so that we can take a look inside the database at specific data structures, such as the **customers** table.  

	![Confirming the migration at the Windows Azure Portal](Images/image017.png?raw=true)

	_Confirming the migration at the Windows Azure Portal_

1. Enter in your **login credentials**  and click on the **Logon"" button. 

	![Logging In](Images/image018.png?raw=true)

	_Logging In_

1. Notice that in the lower left corner there is a menu item called **Design**. Click on it and validate that you can see the **Customers** table. 

	![Verifying the existence of the customers table](Images/image019.png?raw=true)

	_Verifying the existence of the customers table_

1. Towards the top of the window you will see a **New Query** button. Click on it and type in a simple select query as seen below (**select * from customers**). Then click the **Run** menu item. You should be able to see data for the customers table. 

	![Issuing a query](Images/image020.png?raw=true)

	_Issuing a query_

1. You can also connect to the Windows Azure SQL Database from any running instance of SQL Server Management Studio. You can use it to connect to Windows Azure SQL Database. SQL Server Management Studio is a familiar tool to most developers and can boost productivity tremendously.  Launch SQL Server management studio from any computer connected to the Internet. Click the **Connect button** on **Object Explorer**. as stated earlier in this lab, you will need the **Server Name** as well as the **Login Credentials** to connect to the cloud hosted instance of Windows Azure SQL Database. Click **Connect** when you have entered in this information. 

	![Using SQL Server Management Studio](Images/image021.png?raw=true)

	_Using SQL Server Management Studio_

1. You can write mouseclick on the customers table and select **Script Table As | Select To | New Query Editor Window**. Next, click on the **Execute** toolbar button at the top. You should see the same **customer** information as in the previous step. 

	![Entering the select query](Images/image022.png?raw=true)

	_Entering the select query_

1. The final step to this lab is to get the actual connection string that can be used by client applications. The Windows Azure portal gives this to you with just a simple mouse click. Return back to the **SQL database** selection at the **Windows Azure portal**. Note the selection at the bottom of the portal, **View SQL Database connection strings for ADO .Net, ODBC, PHP, and JDBC**. Click on it. 

	![Getting the connection string](Images/image023.png?raw=true)

	_Getting the connection string_

1. you now have all the needed information to connect up to your Windows Azure SQL database. 

	![Viewing all available connection strings](Images/image024.png?raw=true)

	_Viewing all available connection strings_


