---
author: payzer
title: How to turn off scaling
description: 
area: Xbox
---

# How to turn off scaling   
By default, applications are scaled to 200% for XAML and 150% for HTML apps. It is possible to turn off the default scale factor. This will cause your application to use the actual pixel dimensions of the device (1910 by 1080 pixels).   
   
## HTML   
You can opt out of scale factor by using the following code snippet: 
   
`bool result = Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);` 

Or, you can use a web-friendly method:   

```   
@media (max-height: 1080px) {   
    @-ms-viewport {   
        height: 1080px;   
    }   
}   
```

## XAML
You can opt out of scale factor by using the following code snippet:   
   
`bool result = Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);`   
   
## DirectX/C++   
DirectX/C++ applications are not scaled. Automatic scaling only applies to HTML and XAML applications.   


<!--HONumber=Jun16_HO3-->


