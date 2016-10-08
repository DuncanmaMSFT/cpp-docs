---
title: "Displaying Assertions"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: 9
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Displaying Assertions
If the client connected to your service appears to stop responding, the service may have asserted and displayed a message box that you are not able to see. You can confirm this by using Visual C++'s debugger to debug your code (see [Using Task Manager](../VS_visualcpp/Using-Task-Manager.md) earlier in this section).  
  
 If you determine that your service is displaying a message box that you cannot see, you may want to set the **Allow Service to Interact with Desktop** option before using the service again. This option is a startup parameter that permits any message boxes displayed by the service to appear on the desktop. To set this option, open the Services Control Panel application, select the service, click **Startup**, and then select the **Allow Service to Interact with Desktop** option.  
  
## See Also  
 [Debugging Tips](../VS_visualcpp/Debugging-Tips.md)