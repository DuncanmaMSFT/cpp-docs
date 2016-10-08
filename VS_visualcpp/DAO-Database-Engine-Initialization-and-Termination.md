---
title: "DAO Database Engine Initialization and Termination"
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
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 10
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
# DAO Database Engine Initialization and Termination
When using MFC DAO objects, the DAO database engine must first be initialized and then terminated before your application or DLL quits. Two functions,             `AfxDaoInit` and             `AfxDaoTerm`, perform these tasks.  
  
### DAO Database Engine Initialization and Termination  
  
|||  
|-|-|  
|[AfxDaoInit](../Topic/AfxDaoInit.md)|Initializes the DAO database engine.|  
|[AfxDaoTerm](../Topic/AfxDaoTerm.md)|Terminates the DAO database engine.|  
  
##  <a name="afxdaoinit"></a>  AfxDaoInit  
 This function initializes the DAO database engine.  
  
```  
  
void AfxDaoInit( );  
throw(  
   CDaoException*  
);  
  
```  
  
### Remarks  
 In most cases, you don't need to call                         `AfxDaoInit` because the application automatically calls it when it is needed.  
  
 For related information, and for an example of calling                         `AfxDaoInit`, see                         [Technical Note 54](../VS_visualcpp/TN054--Calling-DAO-Directly-While-Using-MFC-DAO-Classes.md).  
  
##  <a name="afxdaoterm"></a>  AfxDaoTerm  
 This function terminates the DAO database engine.  
  
```  
  
void AfxDaoTerm( );  
  
```  
  
### Remarks  
 Typically, you only need to call this function in a regular DLL; an application will automatically call                         `AfxDaoTerm` when it is needed.  
  
 In regular DLLs, call                         `AfxDaoTerm` before the                         `ExitInstance` function, but after all MFC DAO objects have been destroyed.  
  
 For related information, see                         [Technical Note 54](../VS_visualcpp/TN054--Calling-DAO-Directly-While-Using-MFC-DAO-Classes.md).  
  
## See Also  
 [Macros and Globals](../VS_visualcpp/MFC-Macros-and-Globals.md)