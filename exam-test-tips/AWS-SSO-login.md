Step 1: Sign in to AWS SSO
Sign in to the AWS SSO console using your AWS account credentials.

Step 2: Access AWS SSO Dashboard
Once you are logged in, you will be on the AWS SSO Dashboard. Here, you can manage your applications and user access.

Step 3: Add an Application
To add an application, click on "Applications" in the left-hand navigation menu.

Step 4: Choose Application Name
Click on the "Add a new application" button to start the process of adding a new application. You will need to choose between adding an AWS SSO Application or an External Application. Select the appropriate option based on the application you want to add.

AWS SSO Application: This option allows you to add AWS services and AWS accounts that are available to your organization.
External Application: This option is used for adding external (non-AWS) applications.
Step 5: Configure Application Settings

If you selected an AWS SSO Application, you'll need to configure the settings for that AWS service or AWS account. This typically involves choosing the AWS account, the role to assume, and specifying any additional permissions.
If you selected an External Application, you'll need to provide information about the application, including the application name, application URL, and the access URL. You may also need to specify the AWS SSO user attributes.
Step 6: Review and Save

Review the configuration settings and ensure they are accurate. Once you are satisfied with the configuration, click on the "Save changes" or "Create" button, depending on your selection.

Step 7: Assign Users or Groups

After saving the application, you will need to assign users or groups to this application. Click on "Assign users" or "Assign groups" to grant access to the application. This step is critical to ensure that the right people have access to the application.

Step 8: Test and Use the Application

The application has been added, configured, and assigned to users or groups. You can now test and use the application. Users should be able to access the application using their AWS SSO credentials without the need to enter separate usernames and passwords.

Keep in mind that the specific steps and options may vary based on the type of application you are adding (AWS SSO Application or External Application). Ensure that you have the necessary permissions in your AWS account to perform these actions within AWS SSO.
