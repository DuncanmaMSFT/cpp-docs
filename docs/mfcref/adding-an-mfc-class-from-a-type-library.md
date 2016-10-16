---
title: "Adding an MFC Class from a Type Library"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes [C++], adding MFC"
  - "MFC, adding classes from type libraries"
  - "type libraries, adding MFC classes from"
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 11
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Adding an MFC Class from a Type Library
Use this wizard to create an MFC class from an interface in an available type library. You can add an MFC class to an [MFC application](../mfcref/creating-an-mfc-application.md), an [MFC DLL](../mfcref/creating-an-mfc-dll-project.md), or an [MFC ActiveX control](../mfcref/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  You do not need to create your MFC project with Automation enabled to add a class from a type library.  
  
 A type library contains a binary description of the interfaces exposed by a component, defining the methods along with their parameters and return types. Your type library must be registered for it to appear in the **Available type libraries** list in the Add Class from Typelib Wizard. See "Inside Distributed COM: Type Libraries and Language Integration" in the MSDN library for more information.  
  
### To add an MFC class from a type library  
  
1.  In either **Solution Explorer** or [Class View](assetId:///8d7430a9-3e33-454c-a9e1-a85e3d2db925), right-click the name of the project to which you want to add the class.  
  
2.  From the shortcut menu, click **Add**, and then click **Add Class**.  
  
3.  In the [Add Class](../ide/add-class-dialog-box.md) dialog box, in the Templates pane, click **MFC Class from Typelib**, and then click **Open** to display the [Add Class from Typelib Wizard](../mfcref/add-class-from-typelib-wizard.md).  
  
 In the wizard, you can add more than one class in a type library. Likewise, you can add classes from more than one type library in a single wizard session.  
  
 The wizard creates an MFC class, derived from [COleDispatchDriver](../mfcref/coledispatchdriver-class.md), for each interface you add from the selected type library. `COleDispatchDriver` implements the client side of OLE automation.  
  
## See Also  
 [Automation Clients](../mfc/automation-clients.md)   
 [Automation Clients: Using Type Libraries](../mfc/automation-clients--using-type-libraries.md)