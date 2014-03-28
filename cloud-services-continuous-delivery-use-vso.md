<properties linkid="dev-net-common-tasks-publishing-with-vso" urlDisplayName="Publishing with TFS" pageTitle="Continuous delivery with Visual Studio Online in Windows Azure" metaKeywords="" description="Learn how to configure your Visual Studio Online team projects to automatically build and deploy to Windows Azure web sites or cloud services." metaCanonical="" services="web-sites" documentationCenter=".NET" title="Continuous delivery to Windows Azure using Visual Studio Online" authors=""  solutions="" writer="ghogen" manager="" editor=""  />


//taowu-msft made a change

# Continuous delivery to Windows Azure using Visual Studio Online

Visual Studio Online (previously Team Foundation Service) is a cloud-hosted service version of Microsoft's popular Team Foundation Server (TFS) software that provides highly customizable source code and build management, agile development and team process workflow, issue and work item tracking, and more.  You can configure your Visual Studio Online team projects to automatically build and deploy to Windows Azure web sites or cloud services.  For information on how to set up a continuous build and deploy system using an on-premises Team Foundation Server, see [Continuous Delivery for Cloud Services in Windows Azure](../cloud-services-dotnet-continuous-delivery).

This tutorial assumes you have Visual Studio 2013 and the Windows Azure SDK installed. If you don't already have Visual Studio 2013, download it by choosing the **Get started for free** link at [www.visualstudio.com](http://www.visualstudio.com). Install the Windows Azure SDK from [here](http://go.microsoft.com/fwlink/?LinkId=239540).

To set up a cloud service to automatically build and deploy to Windows Azure by using Visual Studio Online, follow these steps:

-   [Step 1: Sign up for Visual Studio Online.][]

-   [Step 2: Check in a project to source control.][]

-   [Step 3: Connect the project to Windows Azure.][]

-   [Step 4: Make changes and trigger a rebuild and redeployment.][]

-   [Step 5: Redeploy an earlier build (optional)][]

-   [Step 6: Change the Production deployment (cloud services only)][]

<h2> <a name="step1"></a><span class="short-header">Sign up for Visual Studio Online</span>Step 1: Sign up for Visual Studio Online</h2>

1. Create a Visual Studio Online account by navigating to [http://www.visualstudio.com](http://www.visualstudio.com). Click the **Sign In** link.
  You will need to sign-in using a Microsoft account. If this is the first time you've signed in, you are asked to provide some information about yourself, such as your name and email address.
![][0]
  
2. If this isn't the first time you've signed in, you see this screen when you sign in. Click the **Create a free account now** link.<br/>
![][36]

3. Create an account URL for your new project. Your account will have the form: https://&lt;accountname&gt;.visualstudio.com.<br/>
![][37]
 
4. Now you can create your first project. Enter the project name and description. Choose the version control system you want to use. Team Foundation Version Control (TFVC) or Git are both supported.  You can find out more about these options at [Use version control](http://go.microsoft.com/fwlink/?LinkId=324037). This walkthrough assumes you are using TFVC. Then choose the process template your organization uses, and choose the **Create Project** button. For more information about process templates, see [Work with team project artifacts, choose a process template](http://go.microsoft.com/fwlink/?LinkId=324035).<br/>
![][1]

5. When project creation is done, click the **Open with Visual Studio to connect** button to automatically launch Visual Studio connected to your team project. If you see any security dialog boxes, choose Allow.<br/>
![][2]

<h2><a name="step2"> </a><span class="short-header">Check in a project to source control.</span>Step 2: Check in a project to source control</h2>

1. In Visual Studio, open the solution you want to deploy, or create a new one.
You can deploy a web site or a cloud service (Windows Azure Application) by following the steps in this walkthrough.
If you want to create a new solution, create a new Windows Azure Cloud Service project,
or a new ASP.NET MVC project. Make sure that the project targets .NET Framework 4 or 4.5, and if you are creating a cloud service project, add an ASP.NET MVC web role and a worker role, and choose Internet application for the web role. When prompted, choose **Internet Application**.
If you want to create a web site, choose the ASP.NET Web Application project template, and then choose MVC. See [Get started with Windows Azure and ASP.NET](http://www.windowsazure.com/documentation/articles/web-sites-dotnet-get-started/).

2. Open the context menu for the solution, and select **Add Solution to Source Control**.<br/>
![][5]

3. Accept or change the defaults and choose the **OK** button. Once the process completes, source control icons appear in Solution Explorer.<br/>
![][6]

4. Open the shortcut menu for the solution, and choose **Check In**.<br/>
![][7]

5. In the Pending Changes area of Team Explorer, type a comment for the check-in and choose the **Check In** button.<br/>
![][8]

<br/>
Note the options to include or exclude specific changes when you check in. If desired changes are excluded, choose the **Include All** link.<br/>
![][9]

<h2> <a name="step3"> </a><span class="short-header">Connect the project to Windows Azure</span>Step 3: Connect the project to Windows Azure</h2>

1. Now that you have a VSO team project with some source code in it, you are ready to connect your team project to Windows Azure.  In the [Windows Azure Portal](http://manage.windowsazure.com), select your cloud service or web site, or create a new one by selecting the + icon at the bottom left and choosing **Cloud Service** or **Web Site** and then **Quick Create**. Choose the **Set up publishing with Visual Studio Online** link.<br/>
![][10]

2. In the wizard, type the name of your Visual Studio Online account in the textbox and click the **Authorize Now** link. You might be asked to sign in.<br/>
![][11]

3. In the OAuth pop-up dialog, choose **Accept** to authorize Windows Azure to configure your team project in VSO.<br/>
![][12]

4. When authorization succeeds, you see a dropdown containing a list of your Visual Studio Online team projects.  Select the name of team project that you created in the previous steps, and choose the wizard's checkmark button.<br/>
![][13]

5. When your project is linked, you will see some instructions for checking in changes to your Visual Studio Online team project.  On your next check-in, Visual Studio Online will build and deploy your project to Windows Azure.  Try this now by clicking the **Check In from Visual Studio** link, and then the **Launch Visual Studio** link (or the equivalent **Visual Studio** button at the bottom of the portal screen).<br/>
![][14]

<h2><a name="step4"> </a><span class="short-header">Trigger a rebuild</span>Step 4: Trigger a rebuild and redeploy your project</h2>

1. In Visual Studio's Team Explorer, click the **Source Control Explorer** link.<br/>
![][15]

2. Navigate to your solution file and open it.<br/>
![][16]

3. In Solution Explorer, open up a file and change it. For example, change the file _Layout.cshtml under the Views\Shared folder in an MVC web role.<br/>
![][17]

4. Edit the logo for the site and hit Ctrl+S to save the file.<br/>
![][18]

5. In Team Explorer, choose the **Pending Changes** link.<br/>
![][19]

6. Type in a comment and choose the **Check In** button.<br/>
![][20]

7. Choose the Home button to return to the Team Explorer home page.<br/>
![][21]

8. Choose the **Builds** link to view the builds in progress.<br/>
![][22]
<br/>
The Team Explorer shows that a build has been triggered for your check-in.<br/>
![][23]

9. Double-click the name of the build in progress to view a detailed 
