# Module 5 - Lab 2 - Exercise 2 - Monitor and Troubleshoot Office 365  

In this exercise you will be introduced to some troubleshooting tools in Office 365, and you will analyze Adatum’s Office 365 service health. 

### Task 1 - Troubleshoot Mail Flow in Office 365  

This task guides you though a variety of tools used to troubleshoot different mail conflict scenarios. To prepare yourself for mail flow problems that may occur within Adatum’s Exchange environment, you have decided to create a test scenario to analyze some of the troubleshooting options available to you. 

1. Switch to your Domain Controller (LON-DC1) VM. You should still be logged into Microsoft 365 as Holly Dickson.

2. In **Internet Explorer**, select the **Office 365 home page** tab, which should still be open (if not, navigate to **https://portal.office.com** and log in as **Holly@M365xZZZZZZ.onmicrosoft.com** and **Pa55w.rd**).

3. In the **Office 365 home page,** select **Outlook.**

4. In Holly’s mailbox, at the top of the left-hand navigation pane, select +**New message** to create a new email.

5. In the **To** text box, type **user@alt.none**. 

6. Enter a subject and some body text and then send the email. 

7. Wait for the delivery failure message to appear in Holly’s Inbox, then double-click the message to open it in a new window. This will make it easier to copy the text of the message in the next step. 

8. In the **Underliverable: {subject of message}** window, select the text in the body of the message starting after “**Original message headers**” through the end of the message. With this text selected, press **Ctrl+C** to copy it to the clipboard. 

9. Close the message window.

10. Open a new tab in your web browser and browse to **testconnectivity.microsoft.com**. 

11. On the **Microsoft Remote Connectivity Analyzer** page, below the announcement at the top of the page, select the **Message Analyzer** tab. 

12. Under **Message Header Analyzer**, paste the message, and then select **Analyze headers**. <br/>

	**Important:** Note the diagnostic information and the time taken for the message to be rejected. SMTP message headers contain a wealth of information which allows you to determine the origins of a message and how it made its way through one or more SMTP servers to its destination. Here’s a quick summary:

	- **Summary section**: Displays the most important properties and total delivery time at a quick glance.

	- **Received headers section**: Displays the more important header properties and delivery time. Enables you to analyze the received headers and displays the longest delays quickly for each discovery of sources of message transfer delays.

	- **Other headers section**: Enables you to quickly detect where the longest message transfer delays occurred. You can sort all headers by occurrence number, name or value.   

	The primary problem in this example is that the domain of the email address **(@alt.none**) does not exist. Normally this is caused by a typo in the recipient’s domain name that needs to be corrected to resolve the issue. 

13. Select **Clear** to reset the Message Header Analyzer window. 

14. Return to Holly’s **Mail** tab. 

15. Select **New** **Message**, and then in the **To** text box, type **difflop8675399@outlook.com**. 

16. Enter a subject and some body text, and then select **Send**. 

17. Wait for the delivery failure message to appear. When the message appears in Holly’s Inbox, double-click the message to open it in a separate window. 

18. In the **Underliverable: {subject of message}** window, select the text in the body of the message starting after “**Original message headers**” through the end of the message. With this text selected, press **Ctrl+C** to copy it to the clipboard. 

19. Close the message window.

20. Switch to the **Microsoft Remote Connectivity Analyzer** tab. 

21. On the **Microsoft Remote Connectivity Analyzer** page, ensure that you are on the **Message Analyzer** tab. 

22. Under **Message Header Analyzer**, paste the message, and then select **Analyze headers**. <br/>

	**Note:** Review the diagnostic information and the time taken for the message to be rejected. In the prior email, the domain of the email address did not exist. In this email, the domain (outlook.com) was valid, but the user mailbox (**difflop8675399@outlook.com**) does not exist. 

23. Close the **Microsoft Remote Connectivity Analyzer** tab in Internet Explorer. 

24. Select the **Microsoft Office Home** tab in Internet Explorer and then select **Admin**. 

25. On the **Microsoft 365 admin center** page, in the left-hand navigation pane, select **Show all**. 

26. Scroll down through left-hand navigation pane, and under **Admin centers,** select **Exchange**. This will open the Exchange Admin Center.

27. On the **Exchange Admin Center**, in the left-hand navigation pane, select **mail flow**. 

28. In the **mail flow** window, select **message trace** in the menu bar at the top of the page. 

29. In the **message trace** window, in the **Date range** field, select the drop-down arrow and select **Past 24 hours**. 

30. In the **Delivery status** field, select the drop-down arrow and select **Failed**.

31. Scroll to the bottom of the page. To the right of the **Sender** field, select **add sender**. 

32. In the **Select Members** window, in the list of users, select **Holly Dickson**, select **add-&gt;,** and then select **OK**.<br/>

	**Note:** If no names appear in the list when the window first opens, select the **Refresh** icon above the **Display name** field. 

33. At the bottom of the page, select the **search** button. 

34. In the **Message Trace Results** window that appears, if no failed message deliveries appear in the list, you may need to wait several minutes before selecting the **Refresh** icon that appears above the item list. 

35. Double-click on each failed message to view the sender, recipient, message size, ID, and IP address information, as well as the **HOW TO FIX IT** instructions.

36. Close the Message Trace Results window. This will return you to the Exchange admin center.

37. Remain signed into Office 365 as Holly. 

  

### Task 2 - Monitor Service Health and Analyze Reports 

Adatum is concerned with the service health issues that have recently come to light throughout the organization They have asked you to review several of the key service health queries and reports so that you can analyze the issues facing the company.

1. On the LON-DC1 VM, in the **Office 365 Home** page, select **Admin**. 

2. In Internet Explorer, select the **Microsoft 365 admin center** tab. 

3. In the left-hand navigation pane, select **Health** and then select **Service health**. 

4. On the right side of the page, select **View history** (depending on your monitor, you may need to scroll to the far right of the window to see **View history**). 

5. The default option is to display a list of items from the last 7 days. Select any entry in the list to see further details about incident. Close the incident window when you’re done reviewing it. 

6. In the left-hand navigation pane, select the **Home** icon. 

7. In the **Office 365 admin center**, on the left-hand navigation pane, select **Reports**, and then select **Usage.** 

8. On the **Usage** page, scroll down and view the **Email activity** chart.  <br/>

	‎**Note:** There might be little or no data shown because there is not much mailbox usage in the lab environment. 

9. At the top of the page, select the **Select a report** drop-down arrow, select **Exchange**, and then select **Mailbox usage**. 

10. Select the different date views to see how the display changes: **7 days**, **30 days**, **90 days** and **180 days**. 

11. In top left of the report, select the drop down (currently showing **Mailbox usage**), select **SharePoint** to further expand the dropdown, and then select **Site usage**. 

12. Select the different date views to see how the display changes: **7 days**, **30 days**, **90 days** and **180 days**. 

13. You now want to look at the reports that are available in the **Security &amp; Compliance center**. In your browser, select a new tab and then enter the following URL in the address bar: **https://protection.office.com.** 

14. In the **Security &amp; Compliance center**, scroll down in the left-hand navigation pane and select **Reports,** and then under the **Reports** section, select **Dashboard.** 

15. Scroll down to any of the reports that have data displayed and click in the chart area to open the **Report Viewer** for that report. 

16. After reviewing the report, select **Dashboard** in the left-hand navigation pane (under the **Reports** section) to return to the report dashboard.

17. Repeat these last two steps for any other report that has data displayed.
 

### Task 3 – Submit a Help Request to Microsoft Support

With Microsoft 365, if you ever run into a situation where you need assistance with a problem, you must submit a service request with the Microsoft Support team. Adatum has asked that you submit a test request that does not require a call back so that you know how to submit a request should a situation ever arise that requires it.

1. On the LON-DC1 VM, in your Internet Explorer browser, select the **Microsoft 365 admin center** tab.

2. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Support** and then select **New service request**.

3. In the **Need help?** window that appears, in the **Briefly describe your issue** box, type the following and then press Enter: **This is a test of the request system. A call back is not needed.**

4. This displays a list of recommended articles related to the issue that you entered.

5. If you need further assistance and would like to speak to a Microsoft support agent, at the top of the window select the **headset** icon (the middle icon) to get help from one of the support agents. 

6. Selecting the headset icon opens the **Contact support** window. To complete this request in a real-world environment, you would enter an extended **description**, a **phone number,** an **email address, a preferred method of contact,** and you would attach any necessary documents before selecting **Contact me**.   <br/>

	‎**IMPORTANT:** Do NOT complete this form in your lab environment. If you enter this request with the **Phone** option selected, you will receive a call from a Microsoft 365 support representative.  
	
7. Since this is the end of Lab 2, close Internet Explorer and any other applications that you may have open (such as PowerShell). Leave your LON-DC1 VM open for the next lab.  
‎  
‎

# End of Lab 2
