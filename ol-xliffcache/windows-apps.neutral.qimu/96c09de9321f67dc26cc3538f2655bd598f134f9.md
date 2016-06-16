---
author: mcleanbyron
ms.assetid: bb105fbe-bbbd-4d78-899b-345af2757720
description: Learn how to add application ID and ad unit ID values from the Windows Dev Center dashboard to your app before you submit your app to the Store.
title: Set up ad units in your app

---

# Set up ad units in your app


\[ Updated for UWP apps on Windows 10. For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

When you use an [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) or [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) to display ads in your app, you must specify an application ID and ad unit ID. While you are developing your app, use the appropriate [test application ID and ad unit ID values](test-mode-values.md) to see how your app renders ads during testing.

After you finish testing your app and you are ready to submit it to Windows Dev Center, you must update your app code to use application ID and ad unit ID values from the [Windows Dev Center dashboard](https://msdn.microsoft.com/library/windows/apps/mt170658.aspx). If you try to use test values in your live app, your app will not receive live ads.

To set up the application ID and ad units for your live app:

1.  On the Windows Dev Center dashboard, select your app and then click **Monetization > Monetize with ads**.
2.  In the **Microsoft Advertising ad units** section on this page, create an ad unit. For the ad unit type, select **Banner** if you are using an **AdControl**, or select **Video interstitial** if you are using an **InterstitialAd**. For more information about this page, see [Monetize with ads](../publish/monetize-with-ads.md).

3.  For each generated ad unit, you will see an **Application ID** and an **Ad unit ID** on this page. To show ads in your app, you'll need to use these values in your apps code:

    * If your app shows banner ads, assign these values to the **ApplicationId** and **AdUnitId** properties of your **AdControl** object.

    * If your app shows video interstitial ads, pass these values to the **RequestAd** method of your **InterstitialAd** object.

> **Important**   If your app uses ad mediation to show banner ads from Microsoft (that is, it uses an **AdMediatorControl** object), you do not need to request ad units. In this scenario, ad units are automatically generated for you. For more information, see [What is the difference: AdMediatorControl or AdControl](what-is-the-difference-admediatorcontrol-or-adcontrol.md).

 

## Related topics

[Test mode values](test-mode-values.md)


 

 


<!--HONumber=Jun16_HO3-->


