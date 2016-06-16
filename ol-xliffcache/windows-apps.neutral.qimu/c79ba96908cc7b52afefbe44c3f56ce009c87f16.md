---
author: mcleanbyron
ms.assetid: 63A9EDCF-A418-476C-8677-D8770B45D1D7
description: The Microsoft Store Engagement and Monetization SDK gives you several ways to monetize your app with ads.
title: Display ads in your app
---

# Display ads in your app


\[ Updated for UWP apps on Windows 10. For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

The [Microsoft Store Engagement and Monetization SDK](monetize-your-app-with-the-microsoft-store-engagement-and-monetization-sdk.md) gives you several ways to monetize your app with ads.

## Display banner and video interstitial ads using the Microsoft advertising libraries

Make more money from your Windows apps by including banner and video interstitial ads. The ads show in Windows apps for PCs, tablets, and phones. You can monitor your ad performance in real time by using the Windows Dev Center dashboard.

To include ads in your apps, use the **AdControl** and **InterstitialAd** controls in the advertising libraries that are distributed in the Microsoft Store Engagement and Monetization SDK. You can use these controls to show banner and video interstitial ads from Microsoft in your XAML or JavaScript/HTML apps for Windows 10, Windows 8.1, Windows Phone 8.1 and Windows Phone 8.

For more information, see [Display ads using the Microsoft advertising libraries](display-ads-using-the-microsoft-advertising-libraries.md). After you publish an app with ads, use the [advertising performance report](../publish/advertising-performance-report.md) to track the performance of the ads.                                           

## Use ad mediation for banner ads from multiple ad networks

You can use the **AdMediatorControl** class in your XAML apps to optimize your advertising revenue by displaying banner ads from multiple ad networks. After you add this control to your app, you configure your ad mediation settings on the Windows Dev Center dashboard, and we take care of mediating banner ad requests from the ad networks you choose. For more information, see [Use ad mediation to maximize ad revenue](use-ad-mediation-to-maximize-revenue.md).

## Differences between the Microsoft advertising libraries and ad mediation

The Microsoft Store Engagement and Monetization SDK includes the libraries for Microsoft advertising and ad mediation. However, these libraries provide different classes and serve different purposes.

* Use the **AdControl** and **InterstitialAd** classes in the Microsoft advertising libraries if you want to display banner or video interstitial ads in a XAML or JavaScript app.
* Use the **AdMediatorControl** class in the ad mediation libraries if you want to display banner ads from multiple ad networks in a XAML app.

For more information, see [What is the difference: AdMediatorControl or AdControl](what-is-the-difference-admediatorcontrol-or-adcontrol.md).

## Related topics

* [Microsoft Store Engagement and Monetization SDK](monetize-your-app-with-the-microsoft-store-engagement-and-monetization-sdk.md)
* [Monetize your app with ads]( http://go.microsoft.com/fwlink/p/?LinkId=699559)


<!--HONumber=Jun16_HO3-->


