---
title: "Compiler Error C2801"
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
ms.topic: error-reference
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
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
# Compiler Error C2801
'operator operator' must be a non-static member  
  
 The following operators can be overloaded only as nonstatic members:  
  
-   Assignment `=`  
  
-   Class member access `->`  
  
-   Subscripting `[]`  
  
-   Function call `()`  
  
 Possible C2801 causes:  
  
-   Overloaded operator is not a class, structure, or union member.  
  
-   Overloaded operator is declared `static`.  
  
-   The following sample generates C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```