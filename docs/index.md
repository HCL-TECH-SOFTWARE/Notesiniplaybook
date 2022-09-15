# INI Playbook Manual

## Overview:

The INI Playbook application helps the Administrators and business users to enable and disable the
INI debug parameters on the user’s Notes client for the troubleshooting purpose. It also helps to track
the status of Notes client debugging of all users. The application is easy to use for both Administrators
and business users. The following steps explains how to use this application.

1. The Administrator user should have the “Admin” role enabled in the database ACL. The business
    users shouldn’t have the “Admin” role enabled.
2. You need to deploy this database on Domino server and sign it with a trusted ECL Signer ID, so
    that the business users don’t get the ECL alert when they use this database on Notes client.
3. Login with Administrator ID on Notes client and open the database. You will see the following
    screen.


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


6. **INI Settings** – This is a lookup view which stores the category and its related INI debug
    parameters which will be used for client debugging purpose. The category column is pulled into a
    Listbox on the Form which is created using “Create New” button on the “All User Docs” view.
    Click on any document to preview the information in the right-side frame. Some categories are
    already pre-stored in this database.
7. You can also create your own category by clicking on “Create New” button on the “INI Settings”
    view. A sample is shown below. To add multiple parameters in same document, press ENTER key
    after typing each parameter as shown below.


8. **My Documents** – This view shows the User Settings documents of the current logged-in user. The
    business user can check his / her user settings documents here with category, status and enabled
    / disabled date and time. The business user can also enable / disable the client debugs by editing
    the document and clicking on Enable / Disable button.
9. To create a User Settings document for Notes client debugging, Go to “All User Docs” and click on
    “Create New” button. It opens the following Form.
10. Click on “User Name(s)” field label and choose the business user’s name from the Address Book
    or just start typing in the username in the field and press Tab key once the username is auto


```
populated. You can also add multiple users in this field. The default maximum user names that
can be submitted at a time is set to 25. You should not add Group name in this field. If multiple
users are selected at a time, then same category will be applied to all. If each user needs separate
category, then you need to create separate user settings document for each user.
```
11. You can change the default maximum user names value by editing profile document named
    “AppProfile”. Create a formula agent with following formula, set Target to None in Agent
    Properties, save agent and run this agent from Action menu in Notes client. It will open the
    Profile document. Change the value and save the document.

```
@Command([EditProfile];"AppProfile");
```
12. Click on “Category” field and select a category from the Listbox for which you need to do Notes
    client debugging.


13. You can add some comments or support case number (if any) in the “Comments” field. This is an
    optional field and can be left blank.
14. Click on “Create User Documents” button. When you submit this form, it creates a user settings
    document for the selected user and category. It also triggers an Email to the business user with
    doc link to the User Settings document. If multiple users are added at a time, then separate User
    Settings documents are created and separate Emails are triggered to each user which were added
    in the Form.
15. You can check the created User Settings document in the “All User Docs” view.


16. The business user will receive an Email with subject format “Notes Client Troubleshooting for
    Category_Name” and the body contains a doc link to the User Settings document.
17. When the business user clicks on the doc link, it opens the User Settings document in the
    database.


18. The business user clicks on the “Enable” button to enable the client debugging for the selected
    category. A message box pops up saying “Client debugging has been enabled. Please restart your
    Notes client”. The INI parameters are now added to the user’s local notes.ini file. The business
    user should restart the Notes client, so that the INI parameters can take effect.
19. Now the Admin or business user can reproduce the issue on Notes client and collect the logs for
    the support.
20. Once the logs are collected, business user can disable the INI debugs by going back to the same
    User settings document through doc link provided in the Email or by going to the “INI Playbook”
    database in the “My Documents” view and opening the User Settings document.
21. Alternatively, Admin can send an email notification to the business user to disable the settings.
    Admin needs to open the User Settings Document and click on “Send Mail to Disable” button.


22. This will trigger an email to the business user with doc link of User Settings document in the mail
    body.
23. The business user can also access the User Settings documents from the “My Documents” view. It
    is in Active status and shows the Enabled Date/Time.
24. The business user will open this User Settings document and clicks on “Disable” button to disable
    the client debugging. It will remove the INI parameters corresponding to the category from the
    user’s local notes.ini file which was added earlier.


25. A message box pops up saying “Client debugging has been disabled. Please restart your Notes
    client”. The business user should restart the Notes client, so that the removal of INI parameters
    can take effect.
26. The status of the disabled category changes to “Obsolete” and the Disabled Date/Time is
    captured.

```
This completes the manual of the INI Playbook application.
```


