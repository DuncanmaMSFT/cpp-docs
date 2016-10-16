---
title: "EventSource::Remove Method"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::Remove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Remove method"
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: 4
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# EventSource::Remove Method
Deletes the event handler represented by the specified event registration token from the set of event handlers associated with the current EventSource object.  
  
## Syntax  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### Parameters  
 `token`  
 A handle that represents an event handler. This token was returned when the event handler was registered by the [Add()](../windows/eventsource--add-method.md) method.  
  
## Return Value  
 S_OK if successful; otherwise, an HRESULT that indicates the error.  
  
## Remarks  
 For more information about the EventRegistrationToken structure, see the Windows::Foundation::EventRegistrationToken Structure topic in the Windows Runtime reference documentation.  
  
## Requirements  
 **Header:** event.h  
  
 **Namespace:** Microsoft::WRL