# Practice Lab: Manage Entra ID device registration

## Summary

In this lab, you will perform Entra ID device registration using a Windows device.

## Exercise 1: Configuring Entra device registration

### Scenario

Several users have asked to use their personal iOS, Android, and Windows devices to access Contoso cloud resources. Since Contoso does not own the devices, you do not want to have the users perform an Entra join for full device management. Instead, you need to ensure that users are able to register their devices with Entra, which still allows you to apply company policy to apps as needed, and still permit users to access Contoso resources. You will test out Entra device registration using a Windows 11 device.

### Task 1: Configure Microsoft Entra device registration

1. On **SEA-SVR1**, if necessary, sign in as **Contoso\\Administrator** with the password of **Pa55w.rd** and close **Server Manager**.

2. On the taskbar select **Microsoft Edge**, in the address bar type **https://entra.microsoft.com**, and then press **Enter**.

3. Sign in as user **<inject key="AzureAdUserEmail"></inject>**, and use the tenant Admin password **<inject key="AzureAdUserPassword"></inject>**, If the **Stay signed in?** prompt appears, select **No**. 

   > The Microsoft Entra admin center opens.

4. In the Microsoft Entra admin center, in the navigation pane, expand **Identity**.

5. Select **Devices** > **All devices**. 

6. On the **Devices | All devices** page, select **Device settings**.

7. On the **Devices|Device settings** page, in the details pane, verify that **Users may register their devices with Azure AD** is set to **All** and is greyed out.

   > This option is greyed out and set to **All** by default when Microsoft Intune is enable in the tenant. This ensures that all users are able to register Windows 10 or newer personal, iOS, Android, and macOS devices with Azure AD.

### Task 2: Perform Entra registration

1. Switch to **HOSTVM** and sign in to **SEA-WS1** VM through desktop shortcut as **Admin** with the password of **Pa55w.rd**.

2. On the taskbar, select **Start** and then select **Settings**.

3. In the **Settings** window, select **Accounts**.

4. On the Accounts page, select **Access work or school**.

5. In the **Access work or school** page, select **Connect**.

6. In the **Microsoft account** window, in the Email address box, enter **`JoniS@yourtenant.onmicrosoft.com`** and then select **Next**.

7. On the **Enter password** page, enter the tenant password provided by your instructor **Pa55-w.rd!** and then select **Sign in**.

8. On the **You're all set!** page, select **Done**.

9. On the **Access work or school** page, verify that Joni's Work or school account is displayed.

10. Close the **Settings** page.

### Task 3: Validate Entra registration

1. On SEA-WS1, right-click **Start**, and then select **Windows Terminal (Admin)**. At the User Account Control, select **Yes**.

2. In the PowerShell console, type the following and press **Enter**: 

    ```
    dsregcmd /status
    ```

3. In the output under **User State**, verify that **WorkplaceJoined : YES** is displayed. This indicates that the user has performed a device registration in Microsoft Entra.

4. Close PowerShell and then sign out of SEA-WS1.

5. Switch to **SEA-SVR1**.

6. In Microsoft Edge, in the Microsoft Entra admin center, expand **Identity**.

7. Select **Devices**, then select **All devices**. In the Devices pane, notice that SEA-WS1 is listed. 

8. Verify that the **Join Type** is listed as **Microsoft Entra registered** and that the owner is **Joni Sherman**. 

   Notice that the device is Microsoft Entra registered, NOT Microsoft Entra joined. Entra registered devices are typically devices that cannot be Entra joined, or devices that are personally owned by the user. Registering a device will provide access to Cloud based resources.

9. Close Microsoft Edge.

### Task 4: Sign in to Windows and disconnect from the organization

1. Switch to **HOSTVM** and attempt to sign in to **SEA-WS1** as **`JoniS@yourtenant.onmicrosoft.com`**.

   >**Note**: Notice that unlike Entra Joined devices, an Entra registered device does not allow a user to sign in to the device with an Entra credential

2. On SEA-WS1, sign in as **Admin** with the password of **Pa55w.rd**. 

3. Select **Start** and then select **Settings**.

4. In the **Settings** window, select **Accounts**.

5. On the Accounts page, select **Access work or school**.

6. In the **Access work or school** page, select the **JoniS** Work or School account.

7. Next to Disconnect this account, select **Disconnect** and then select **Yes**.

   > Notice that you do not have to restart to disconnect a registered device from Microsoft Entra.

8. Sign out of SEA-WS1.

**Results**: After completing this exercise, you will have configured Entra device registration.

**END OF LAB**
