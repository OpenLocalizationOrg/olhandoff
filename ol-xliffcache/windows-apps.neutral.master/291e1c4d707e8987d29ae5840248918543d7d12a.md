---
author: mcleanbyron
ms.assetid: 9165f709-71d7-42cf-9b30-3190fe029fb4
description: Learn about the differences between the AdControl class in the Microsoft advertising libraries and the AdMediatorControl class in the ad mediation libraries.
title: What is the difference - AdMediatorControl or AdControl
---

# What is the difference: AdMediatorControl or AdControl


\[ Updated for UWP apps on Windows 10. For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Use the Microsoft advertising libraries for XAML and JavaScript in your app when you want to display banner ads or video interstitial ads from Microsoft. These libraries are different than the ad mediation libraries, which you use to display ads from multiple ad networks. Use this documentation for the Microsoft advertising libraries (XAML and JavaScript) when:

* You are using [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) or [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) in a XAML or JavaScript app rather than **AdMediatorControl**.
* You are looking for reference information for the underlying **AdControl** API used by ad mediation.

The Microsoft advertising libraries and the ad mediation libraries are both included in the Microsoft Store Engagement and Monetization SDK. For more information about installing this SDK and the different Microsoft advertising libraries that are included in this SDK, see [Install the Microsoft advertising libraries](install-the-microsoft-advertising-libraries.md).

>**Note**  To show interstitial ads, use the **InterstitialAd** control. The **AdControl** and **AdMediatorControl** cannot show interstitial ads. For more information, see [Interstitial ads](interstitial-ads.md).

 

## Ad mediation


The recommended way to show banner ads from Microsoft (not interstitial ads) is to use the **AdMediatorControl** in your app. The **AdMediatorControl** shows banner ads from multiple advertising networks.

When you use the **AdMediatorControl** in a project, you must specify which ad networks to use using the **Connected Services** feature of Visual Studio. Visual Studio will attempt to fetch the required assemblies programmatically for some ad networks. If there are any assemblies that cannot be automatically retrieved, you must install them for each ad network. For more information about ad mediation, see [Use ad mediation to maximize revenue](use-ad-mediation-to-maximize-revenue.md).

The **AdMediatorControl** abstracts away the use of ad unit ids and application ids. Those ids are managed by the **AdMediatorControl**, in conjunction with your ad mediation settings in the Windows Dev Center dashboard. For more information, see [Submit your app and configure ad mediation](submit-your-app-and-configure-ad-mediation.md).

The **AdMediatorControl** supports the APIs for each of the advertising services it mediates using its own attributes and syntax. For more information, see [Add and use the ad mediator control](add-and-use-the-ad-mediator-control.md).

## AdControl


If you only want to display banner ads from Microsoft (no other ad networks), you can use **AdControl** by itself in XAML and JavaScript apps. While testing an app that uses the **AdControl**, use the [Test mode values](test-mode-values.md) for the application ID and ad unit ID. After you have finished testing your app and you are ready to submit it to Windows Dev Center, use the Windows Dev Center dashboard to get your live ad unit ID and application ID and update your code to use these values. For more information, see [Set up ad units in your app](set-up-ad-units-in-your-app.md).

 

 


<!--HONumber=Jun16_HO2-->


