---
title: "hash_multiset::make_value (STL-CLR)"
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
ms.topic: reference
H1: hash_multiset::make_value (STL/CLR)
ms.assetid: 33a4df1c-5451-44f2-af2e-a8419f9be3b9
caps.latest.revision: 6
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
# hash_multiset::make_value (STL-CLR)
Constructs a value object.  
  
## Syntax  
  
```  
static value_type make_value(key_type key);  
```  
  
#### Parameters  
 key  
 Key value to use.  
  
## Remarks  
 The member function returns a `value_type` object whose key is `key`. You use it to compose an object suitable for use with several other member functions.  
  
## Example  
  
```  
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requirements  
 **Header:** <cliext/hash_set>  
  
 **Namespace:** cliext  
  
## See Also  
 [hash_multiset (STL/CLR)](../VS_visualcpp/hash_multiset--STL-CLR-.md)   
 [hash_multiset::key_type (STL/CLR)](../VS_visualcpp/hash_multiset--key_type--STL-CLR-.md)   
 [hash_multiset::value_type (STL/CLR)](../VS_visualcpp/hash_multiset--value_type--STL-CLR-.md)