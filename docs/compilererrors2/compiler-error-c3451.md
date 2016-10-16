---
title: "Compiler Error C3451"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "error-reference"
f1_keywords: 
  - "C3451"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3451"
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: 13
ms.author: "corob"
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
# Compiler Error C3451
'attribute': cannot apply unmanaged attribute to 'type'  
  
 A C++ attribute cannot be applied to a CLR type. See [C++ Attributes Reference](../windows/c---attributes-reference.md) for more information.  
  
 For more information, see [User-Defined Attributes](../windows/user-defined-attributes---c---component-extensions-.md).  
  
 This error can be generated as a result of compiler conformance work that was done for Visual C++ 2005: the [uuid](../windows/uuid--c---attributes-.md) attribute is no longer allowed on a user-defined attribute using CLR programming. Use \<xref:System.Runtime.InteropServices.GuidAttribute> instead.  
  
## Example  
 The following sample generates C3451.  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```