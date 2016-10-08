---
title: "C++ Program Startup and Termination"
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
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 8
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
# C++ Program Startup and Termination
A C++ program performs the same operations as a C program does at program startup and at program termination, plus a few more outlined here.  
  
 Before the target environment calls the function `main`, and after it stores any constant initial values you specify in all objects that have static duration, the program executes any remaining constructors for such static objects. The order of execution is not specified between translation units, but you can nevertheless assume that some [iostreams](../VS_visualcpp/iostreams-Conventions.md) objects are properly initialized for use by these static constructors. These control text streams are:  
  
-   [cin](../Topic/cin.md) — for standard input.  
  
-   [cout](../Topic/cout.md) — for standard output.  
  
-   [cerr](../Topic/cerr.md) — for unbuffered standard error output.  
  
-   [clog](../Topic/clog.md) — for buffered standard error output.  
  
 You can also use these objects within the destructors called for static objects, during program termination.  
  
 As with C, returning from `main` or calling `exit` calls all functions registered with `atexit` in reverse order of registry. An exception thrown from such a registered function calls `terminate`.  
  
## See Also  
 [STL Overview](../VS_visualcpp/C---Standard-Library-Overview.md)   
 [Thread Safety in the C++ Standard Library](../VS_visualcpp/Thread-Safety-in-the-C---Standard-Library.md)