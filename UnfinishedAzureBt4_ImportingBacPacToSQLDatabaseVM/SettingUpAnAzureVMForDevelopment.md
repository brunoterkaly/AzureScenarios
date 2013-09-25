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

1. Go to the [Windows Azure Management Portal](https://manage.windowsazure.com/) and sign in using the Microsoft credentials associated with your subscription. On the left menu, select **Virtual Machines**.

	![Log on to Windows Azure portal](Images/image001.png?raw=true "Log on to the Windows Azure portal")

	_Log on to the Windows Azure Management Portal_

1. Click **New** on the command bar. It is in the lower left corner.

	

1. In the menu located at the bottom, select **New | Compute | Virtual Machine | From Gallery** to start creating a new virtual machine.
	 
	![Creating a new Virtual Machine](Images/image003.png?raw=true)

	_Creating a new Virtual Machine_
 
1. In the **Virtual Machine image Selection** page, click **Platform Images** on the left menu and select the **Visual Studio Ultimate 2013 RC** from the list. Click the arrow to continue.	

	![Creating a new Virtual Machine With Visual Studio Ultimate 2013 RC](images/image006.png?raw=true)

	_Selecting Visual Studio 2013 Ultimate 2013 RC_

1. The next arrow is located in the lower right corner of the portal screen.

	

1. The wizard will start by having you specify a **virtual machine name**. You will also choose the **machine size**. Finally, you will need to know your **user name** and **password** for later, when you log into the machine with **Remote Desktop**.

	![Configuring the VM](Images/image007.png?raw=true)

	_Configuring the VM_

1. You will **Create a new cloud service**. You will also specify:

	- Cloud Service DNS name (see note)
   - Azure subscription to use for the VM (only appears if you have more than one subscription)
	- Region (the data center to host your virtual machine)
	

	
	![Configuring the VM ](Images/image009.png?raw=true)

	_Configuring the VM_

	> **Note:** The URL used for the virtual machine corresponds to a DNS name and is subject to standard DNS naming rules. Moreover, the name is publicly visible and must therefore be unique. The portal ensures that the name is valid by verifying that the name complies with the naming rules and is currently available. A validation error will be shown if you enter a name that does not satisfy the rules.

    > **Note:** If you have more than one Windows Azure Subscription associated with your Microsoft Account, you will also need to choose which subscription you want the Virtual Machine to be created on.  


1. Once the virtual machines have been configured you will configure the public endpoints to allow connections from outside the Windows Azure data center. You will not need to change these values.

	![Endpoint configuration](Images/image011.png?raw=true)

	_Endpoint Configuration_

1. Validating that the virtual machine is running.

	![The virtual machine running](Images/image013.png?raw=true)

	_The virtual machine running_

### Exercise 1: Using Remote Desktop to connect to the Virtual Machine ###

In this section, you will log into the Windows Azure Portal and create an Azure Virtual Machine using the Windows Azure Gallery. 

#### Task 1 – Configuring Visual Studio 2013 RC and SQL Server 2012 Express ####

You will now connect to the Virtual Machine and configure it to run both **Visual Studio 2013 Ultimate RC** and **SQL Server 2013 Express**.

You will also download and install software, such as **SQL Server 2012 Express Management Studio**.

1. You will select the Virtual Machine you just created by clicking on the text, **Running** at the Windows Azure Portal's Virtual Machine section. It will be the VM just created in Task 1.

	Click the **Connect** button in the bottom left menu bar. 

	![The connect button](Images/image015.png?raw=true)

	_The connect button_

1. You will be asked to download the remote desktop settings file. Click **Open** and log on using the credentials you defined when creating the Virtual Machine. 

	![Remoting into the virtual machine](Images/image017.png?raw=true)

	_Remoting into the virtual machine_

1. Once the login is complete and the desktop appears, on the left side click on the shortcut **Configure Development**.

	![Configuring Development](Images/image019.png?raw=true)

	_Configuring Development_

1. The **ConfigureDeveloperDesktop** folder will open up. Click and navigate into the **Scripts** folder.

	![Getting to the scripts folder](Images/image021.png?raw=true)

	_Getting to the scripts folder_

1. Right mouse click on **ConfigureSQLExpress** and choose **Run with Powershell**.

	![Configuring SQL Express](Images/image023.png?raw=true)

	_Configuring SQL Express_

1. This process can take 5 to 15 minutes to complete. At the end, **Visual Studio 2013 Ultimate RC** will appear.

	![Waiting for the configuration to complete](Images/image025.png?raw=true)

	_Waiting for the configuration to complete_

1. You will be asked to login with your **Live ID** once **Visual Studio** appears.

	![Logging into Visual Studio](Images/image027.png?raw=true)

	_Logging into Visual Studio_

1. Select the **View | Server Explorer** menu from **Visual Studio**.

	![Viewing Server Explorer](Images/image029.png?raw=true)

	_Viewing Server Explorer_

	> **Note:** The purpose of this section is to verify **SQL Express** is properly configured.

1. Right mouse click on **Data Connections** and choose **Add Connection**.

	![Connecting to SQL Express](Images/image031.png?raw=true)

	_Connecting to SQL Express_

1. In the **Server Name** name text box, type in **(local)\SQLEXPRESS**. The purpose is to 

	![Verifying connectivity to SQLEXPRESS](Images/image033.png?raw=true)

	_Verifying connectivity to SQLEXPRESS_

1.	In order to enable downloads from Internet Explorer you will need to update **Internet Explorer Enhanced Security Configuration**. In the Azure Virtual Machine, open **Server Manager** from **Start | Administrative Tools | Server Manager**.

 	![Configuring IE ESC](./Images/image035.png?raw=true)
 
	_Configuring IE ESC_

1. In the **Server Manager**, click **Configure IE ESC** within **Security Information** section.


1. In the **Internet explorer Enhanced Security** configuration, turn **off** the enhanced security for **Administrators** and click **OK**.

	![Internet Explorer Enhanced Security(2)](Images/image037.png?raw=true)
	 
	_Internet Explorer Enhanced Security_
 
	>**Note:** Modifying **Internet Explorer Enhanced Security** configurations is not good practice and is only for the purpose of this particular lab. The correct approach should be to download the files locally and then copy them to a shared folder or directly to the Virtual Machine.



1.  For **Administrators**, turn the configuration to **Off**.

	![Shutting configuration off](Images/image039.png?raw=true)

	_Shutting configuration off_

#### Task 2 – Configuring the browser to allow downloads and installation ####

The next section if for downloading and installing **SQL Setup 2012 Express Management Studio**. To be able to download and install this software, you will to change the security settings in Internet Explorer.

1. Start Internet Explorer. Right mouse click in the **title bar area** and choose **Menu bar**. This enable the menus within the browser.

	![Enabling the menu in Internet Explorer](Images/image041.png?raw=true)

	_Enabling the menu in Internet Explorer_

1. From the menu, choose **Tools | Internet Options**.

	![Bringing up the Internet Explorer Dialog Box](Images/image043.png?raw=true)

	_Bringing up the Internet Explorer Dialog Box_

1. Select the **Security** tab.

	![Modifying Internet Explorer security settings](Images/image045.png?raw=true)

	_Modifying Internet Explorer security settings_

1. Scroll down to the **Downloads** section and **Enable .NET Framework setup**.

	![Enabling .NET Framework setup](Images/image047.png?raw=true)

	_Enabling .NET Framework setup_

1. You will now prepare to download **SQL Server 2012 Express** tooling. Use Internet Explorer to navigate to bing.com. Type in **sql server 2012 express download**. Click the official download link.

	![Finding SQL Server 2012 Express download](Images/image049.png?raw=true)

	_Finding SQL Server 2012 Express dowload_

1. Click **Download** from the web page. There will be several options.

	![Downloading SQL Server 2012 Express](Images/image051.png?raw=true)

	_Downloading SQL Server 2012 Express_

1. A download windown will appear at the bottom of Internet Explorer. Select **Save As**. The file **SQLManagementStudio_x64_ENU.exe** will be downloaded to the **Downloads** folder.

	![Downloading SQLManagementStudio_x64_ENU.exe](Images/image053.png?raw=true)

	_Downloading SQLManagementStudio_x64_ENU.exe_

1. Navigate to the **Downloads** folder. Double-click on **SQLManagementStudio_x64_ENU.exe** to begin the installation process.

	![Navigating to the Downloads folder](Images/image055.png?raw=true)

	_Navigating to the Downloads folder. Installing SQL Server 2012 Express Management Studio_

1. You select **New SQL Server stand-alone installation or add features to an existing installation**

	![Adding features to an existing installation](Images/image057.png?raw=true)

	_Adding features to an existing installation_

1. Wait as setup files are installed.

	![Setting up dialog box](Images/image059.png?raw=true)

	_Setting up dialog box_

1. Select **Add features to an existing instancce of SQL Server 2012**. Then click **Next**.

	![Adding features to an existing installation](Images/image061.png?raw=true)

	_Adding features to an existing installation_

1. In the checkboxes below, select **Management Tools - Basic**

	![Intalling the Management Tools](Images/image063.png?raw=true)

	_Intalling the Management Tools_

1. Wait a few minutes. The **Complete** dialog box should appear.

	![A successful installation](Images/image065.png?raw=true)

	_A successful installation_

1. Now that you have successfully installed **SQL Server 2012 Express Management Studio**, you should be able to select it from the **Start** screen.

	![Navigating to the start screen](Images/image067.png?raw=true)

	_Navigating to the start screen_

1. The final step is to verify that we can connect to **(local)\SQLEXPRESS**. This final step concludes this lab and verifies that we now have a development machine with **Visual Studio 2013 Ultimate RC** and **SQL Server 2012 Express**.

	![Final verification of success](Images/image069.png?raw=true)

	_Final verification of success_


