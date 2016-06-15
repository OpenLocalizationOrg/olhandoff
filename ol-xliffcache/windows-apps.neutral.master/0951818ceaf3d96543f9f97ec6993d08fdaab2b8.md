---
author: mcleanbyron
ms.assetid: 3aeddb83-5314-447b-b294-9fc28273cd39
description: Learn about how to install the Microsoft advertising libraries.
title: Install the Microsoft advertising libraries

---

# Install the Microsoft advertising libraries


\[ Updated for UWP apps on Windows 10. For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

The Microsoft advertising libraries for Windows apps are included in the [Microsoft Store Engagement and Monetization SDK](http://aka.ms/store-em-sdk). This SDK is an extension to Visual Studio 2015 and Visual Studio 2013.

For installation instructions, see [Monetize your app and engage customers with the Microsoft Store Engagement and Monetization SDK](https://msdn.microsoft.com/windows/uwp/monetize/monetize-your-app-with-the-microsoft-store-engagement-and-monetization-sdk).

> **Note** If you have installed Windows 10 Anniversary SDK Preview Build 14295 or later with Visual Studio 2015, you must also install the WinJS library if you want to add ads to a JavaScript/HTML app. This library used to be included in previous versions of the Windows SDK for Windows 10, but starting with the Windows 10 Anniversary SDK Preview Build 14295 this library must be installed separately. To install WinJS, see [Get WinJS](http://try.buildwinjs.com/download/GetWinJS/).

## Library names for advertising and ad mediation


The Microsoft Store Engagement and Monetization SDK includes two sets of advertising libraries: the libraries for Microsoft advertising (which provide the [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) and [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx)  classes for XAML and JavaScript/HTML apps) and the libraries for ad mediation libraries (which provide the **AdMediatorControl** class).

This documentation describes how to use the **AdControl** and **InterstitialAd** classes in the Microsoft advertising libraries to display banner or video interstitial ads from Microsoft. For information about using ad mediation, see [Use ad mediation to maximize revenue](https://msdn.microsoft.com/windows/uwp/monetize/use-ad-mediation-to-maximize-revenue).


Before you can use the any of the advertising controls in your app code, you must reference the appropriate library in your project. The following tables lists the names of each of the libraries in the Microsoft Store Engagement and Monetization SDK as they appear in in the **Reference Manager** dialog box in Visual Studio.


<table>
    <thead>
        <tr><th>Control name</th><th>Project type</th><th>Library name in Reference Manager</th><th>Version number</th></tr>
    </thead>
    <tbody>
    <tr>
            <td rowspan="3">**AdControl** and **InterstitialAd** (XAML)</td>
            <td>UWP</td>
            <td>Microsoft Advertising SDK for XAML</td>
            <td>10.0</td>
        </tr>
        <tr>
            <td>Windows 8.1</td>
            <td>Ad Mediator SDK for Windows 8.1 XAML</td>
            <td>1.0</td>
        </tr>
        <tr>
            <td>Windows Phone 8.1</td>
            <td>Ad Mediator SDK for Windows Phone 8.1 XAML</td>
            <td>1.0</td>
        </tr>
    <tr>
            <td rowspan="3">**AdControl** and **InterstitialAd** (JavaScript/HTML)</td>
            <td>UWP</td>
            <td>Microsoft Advertising SDK for JavaScript</td>
            <td>10.0</td>
        </tr>
        <tr>
            <td>Windows 8.1</td>
            <td>Microsoft Advertising SDK for Windows 8.1 Native (JS)</td>
            <td>8.5</td>
        </tr>
        <tr>
            <td>Windows Phone 8.1</td>
            <td>Microsoft Advertising SDK for Windows Phone 8.1 Native (JS)</td>
            <td>8.5</td>
        </tr>
    <tr>
            <td rowspan="3">**AdMediatorControl** (XAML only)</td>
            <td>UWP</td>
            <td>Microsoft Advertising Universal SDK</td>
            <td>1.0</td>
        </tr>
        <tr>
            <td>Windows 8.1</td>
            <td>Ad Mediator SDK for Windows 8.1 XAML</td>
            <td>1.0</td>
        </tr>
        <tr>
            <td>Windows Phone 8.1</td>
            <td>Ad Mediator SDK for Windows Phone 8.1 XAML</td>
            <td>1.0</td>
        </tr>
    </tbody>
</table>

 

 

 


<!--HONumber=Jun16_HO2-->


