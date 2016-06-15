---
author: mcleanbyron
ms.assetid: 2383296e-c3d7-4b49-bcd2-621391228fdb
description: Learn how to handle the events of the AdControl class.
title: AdControl events in JavaScript

---

# AdControl events in JavaScript


\[ Updated for UWP apps on Windows 10. For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

The following examples demonstrate how to handle the events of the [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) class. These examples assume that you have previously assigned the event handlers to the **AdControl** events. For more information about how to do this, see [HTML properties example](html-properties-example.md).

In JavaScript, the **AdControl** events must be enclosed by the [MarkSupportedForProcessing](http://msdn.microsoft.com/en-us/library/windows/apps/Hh967819.aspx) function. For more information about handling events in JavaScript, see [Coding basic apps (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh780660.aspx#adding-event-handlers).

## Examples

``` syntax
WinJS.Utilities.markSupportedForProcessing(
window.myAdError = function (sender, msg) {
  // place code here for when there is an error serving an ad.
  // e.g. you may opt to show a default experience, or reclaim the div for other purposes.
});

WinJS.Utilities.markSupportedForProcessing(
window.myAdRefreshed = function (sender) {
  // place code here that you wish to execute when the ad refreshes.
});

WinJS.Utilities.markSupportedForProcessing(
window.myAdEngagedChanged = function (sender) {
  if (true == sender.isEngaged) {
    // code here for when user engaged with ad, e.g. if a game, pause it.
  }
  else {
    // user no longer engaged with ad, include code to unpause.
  }
});
```

## Related topics

* [Advertising samples on GitHub](http://aka.ms/githubads)
* [AdControl error handling](adcontrol-error-handling.md)
* [RoutedEventArgs Class](http://msdn.microsoft.com/en-us/library/system.windows.routedeventargs.aspx)

 

 


<!--HONumber=Jun16_HO2-->


