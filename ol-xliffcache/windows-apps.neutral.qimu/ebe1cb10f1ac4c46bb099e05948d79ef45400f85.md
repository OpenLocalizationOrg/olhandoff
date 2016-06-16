---
author: payzer
title: How to disable mouse mode
description: 
area: Xbox
---

# How to disable mouse mode
Mouse mode is on by default for all applications. This means all applications that have not opted out will recieve a mouse pointer (similar to the one in the Edge browser on the console). We strongly recommend you turn this off and optimize for directional controller navigation.   
   
## HTML   
To turn off mouse mode, add the following to a JavaScript file in your application:   
   
`navigator.gamepadInputEmulation = "keyboard";`   

## XAML    
To turn off mouse mode, add the following to a JavaScript file in your application:   
   
`this.RequiresPointerMode = Windows.UI.Xaml.ApplicationRequiresPointerMode.WhenRequested;`   

## C++/DirectX   
If you are writing a C++/DirectX app, there's nothing to do. Mouse mode only applies to HTML and XAML applications.


<!--HONumber=Jun16_HO3-->


