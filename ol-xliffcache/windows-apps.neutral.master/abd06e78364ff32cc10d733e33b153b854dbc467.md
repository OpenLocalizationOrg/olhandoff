---
author: payzer
title: How to turn off overscan
description: 
area: Xbox
---

# How to draw UI to the edge of the screen   
By default, applications will have borders placed at the edges of the viewport. This is to account for the TV-safe area. For more information, see [Designing for Xbox and TV](http://go.microsoft.com/fwlink/?LinkID=760736#tv-safe-area).  We recommend turning this off and drawing to the edge of the screen. You can draw to the edge of the screen by adding the following code when your application starts:
   
`Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().SetDesiredBoundsMode(Windows.UI.ViewManagement.ApplicationViewBoundsMode.UseCoreWindow);`
   
Note: C++/DirectX applications do not have to worry about this. The system will always render your application to the edge of the screen.


<!--HONumber=Jun16_HO2-->


