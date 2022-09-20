# Notes INI Playbook Documentation

## Overview:

The Notes INI Playbook application helps the Administrators and line of business users to enable and disable the
INI debug parameters on the user’s Notes client for the troubleshooting purpose. It also helps to track
the status of Notes client debugging of all users. The application is easy to use for both Administrators
and line of business users. The following steps explains how to use this application.

1. The Administrator user should have the “Admin” role enabled in the database ACL. The line of business
    users shouldn’t have the “Admin” role enabled.
    
    ![image](https://user-images.githubusercontent.com/108002256/190377814-5ef75d7a-75f4-4669-9552-c111c27fa3f8.png)

2. You need to deploy this database on Domino server and sign it with a trusted ECL Signer ID, so
    that the business users don’t get the ECL alert when they use this database on Notes client.
    
3. Login with Administrator ID on Notes client and open the database. You will see the following
    screen.
    
    ![image](https://user-images.githubusercontent.com/108002256/190479718-e3af7a2c-2a5c-4761-b3de-e79d9f1ba28b.png)

4. There are four tabs on the left side frame for Administrator. The first two (‘Welcome’ and ‘My
    Documents’) are visible to all business users. The last two (‘All User Docs’ and ‘INI Settings’) is
    kept hidden to business users. Administrator can see all the four tabs.
    
5. **All User Docs** – Click on this tab to open “All User Docs” view in the centre frame. This view
    shows the User Settings documents of all users that are created by Administrator. The
    Administrator can check the category of client debugging, its status and enabled / disabled date
    and time in this view. If you click on any document, you can preview the document in the right-
    side frame. This view contains an action button “Create New”. Click on this button to open a new
    Form. Here you can select username for whom the client debugging needs to be done and can
    select the category for which client debugging needs to be done. You will see this in detail in later
    steps.
    
    ![image](https://user-images.githubusercontent.com/108002256/190480540-1fc04def-8230-4a19-8051-be71c1dafb7c.png)

6. **INI Settings** – This is a lookup view which stores the category and its related INI debug
    parameters which will be used for client debugging purpose. The category column is pulled into a
    Listbox on the Form which is created using “Create New” button on the “All User Docs” view.
    Click on any document to preview the information in the right-side frame. Some categories are
    already pre-stored in this database.
    
    ![image](https://user-images.githubusercontent.com/108002256/190480589-34479e68-5379-4291-ad47-133e1fd855b0.png)

7. You can also create your own category by clicking on “Create New” button on the “INI Settings”
    view. A sample is shown below. To add multiple parameters in same document, press ENTER key
    after typing each parameter as shown below.
    
    ![image](https://user-images.githubusercontent.com/108002256/190480698-60a2d0b2-021e-448c-8d45-f8e8afb7a036.png)

8. **My Documents** – This view shows the User Settings documents of the current logged-in user. The
    business user can check his / her user settings documents here with category, status and enabled
    / disabled date and time. The business user can also enable / disable the client debugs by editing
    the document and clicking on Enable / Disable button.
    
    ![image](https://user-images.githubusercontent.com/108002256/190480731-a5f83374-df64-4cc7-bba6-a1282e29be2a.png)
    
9. To create a User Settings document for Notes client debugging, Go to “All User Docs” and click on
    “Create New” button. It opens the following Form.
    
    ![image](https://user-images.githubusercontent.com/108002256/190480769-87cdabb8-7f29-4130-9bf6-196e1601e270.png)
    
10. Click on “User Name(s)” field label and choose the business user’s name from the Address Book
    or just start typing in the username in the field and press Tab key once the username is auto populated. You can also add multiple users in this field. The default maximum user names that
can be submitted at a time is set to 25. You should not add Group name in this field. If multiple
users are selected at a time, then same category will be applied to all. If each user needs separate
category, then you need to create separate user settings document for each user.

![image](https://user-images.githubusercontent.com/108002256/190480822-ef67b93c-913a-4226-9c19-6c44e00dff80.png)

11. You can change the default maximum user names value by editing profile document named
    “AppProfile”. Create a formula agent with following formula, set Target to None in Agent
    Properties, save agent and run this agent from Action menu in Notes client. It will open the
    Profile document. Change the value and save the document.

```
@Command([EditProfile];"AppProfile");
```
12. Click on “Category” field and select a category from the Listbox for which you need to do Notes
    client debugging.

![image](https://user-images.githubusercontent.com/108002256/190480878-af8bef2c-54c2-44c5-9b8c-93bc3818b192.png)

13. You can add some comments or support case number (if any) in the “Comments” field. This is an
    optional field and can be left blank.

14. Click on “Create User Documents” button. When you submit this form, it creates a user settings
    document for the selected user and category. It also triggers an Email to the business user with
    doc link to the User Settings document. If multiple users are added at a time, then separate User
    Settings documents are created and separate Emails are triggered to each user which were added
    in the Form.

![image](https://user-images.githubusercontent.com/108002256/190480921-274ee4d2-2685-4b23-9fdc-fe508eea6c3b.png)

15. You can check the created User Settings document in the “All User Docs” view.

![image](https://user-images.githubusercontent.com/108002256/190480946-d1394c2d-3c64-4e99-9d2c-9d09f20aefc0.png)

16. The business user will receive an Email with subject format “Notes Client Troubleshooting for
    Category_Name” and the body contains a doc link to the User Settings document.

![image](https://user-images.githubusercontent.com/108002256/190480984-518e799f-6ad3-45d1-8aa8-4d84e5cdd22d.png)

17. When the business user clicks on the doc link, it opens the User Settings document in the
    database.
    
![image](https://user-images.githubusercontent.com/108002256/190481034-7bd390ec-ea07-4a97-b050-15648c3d1c2d.png)

18. The business user clicks on the “Enable” button to enable the client debugging for the selected
    category. A message box pops up saying “Client debugging has been enabled. Please restart your
    Notes client”. The INI parameters are now added to the user’s local notes.ini file. The business
    user should restart the Notes client, so that the INI parameters can take effect.

![image](https://user-images.githubusercontent.com/108002256/190481076-cf2ad6ac-33fe-42d6-a3a0-fcc79b2b095b.png)

19. Now the Admin or business user can reproduce the issue on Notes client and collect the logs for
    the support.

20. Once the logs are collected, business user can disable the INI debugs by going back to the same
    User settings document through doc link provided in the Email or by going to the “INI Playbook”
    database in the “My Documents” view and opening the User Settings document.

21. Alternatively, Admin can send an email notification to the business user to disable the settings.
    Admin needs to open the User Settings Document and click on “Send Mail to Disable” button.
    
![image](https://user-images.githubusercontent.com/108002256/190481100-b081b487-d461-45ea-a071-f235986cf212.png)

22. This will trigger an email to the business user with doc link of User Settings document in the mail
    body.

![image](https://user-images.githubusercontent.com/108002256/190481137-50522cc4-e4f8-419b-aef4-1fcf584b2b25.png)

23. The business user can also access the User Settings documents from the “My Documents” view. It
    is in Active status and shows the Enabled Date/Time.

![image](https://user-images.githubusercontent.com/108002256/190482014-9bf04a7d-6035-472e-9c69-41e677970f80.png)

24. The business user will open this User Settings document and clicks on “Disable” button to disable
    the client debugging. It will remove the INI parameters corresponding to the category from the
    user’s local notes.ini file which was added earlier.

![image](https://user-images.githubusercontent.com/108002256/190481314-7951c76c-ea93-4260-a88f-3c59ddd2ee31.png)

25. A message box pops up saying “Client debugging has been disabled. Please restart your Notes
    client”. The business user should restart the Notes client, so that the removal of INI parameters
    can take effect.

![image](https://user-images.githubusercontent.com/108002256/190481340-934091ea-7184-4c5b-ab3a-bce84ef33cc3.png)

26. The status of the disabled category changes to “Obsolete” and the Disabled Date/Time is
    captured.

![image](https://user-images.githubusercontent.com/108002256/190481373-4527ad9c-5567-40e5-960d-d265631c5e2f.png)

This completes the documentation of Notes INI Playbook application.
