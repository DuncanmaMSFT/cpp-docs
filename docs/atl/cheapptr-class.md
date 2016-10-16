---
title: "CHeapPtr Class"
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
  - "ATL::CHeapPtr"
  - "CHeapPtr"
  - "ATL.CHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtr class"
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
caps.latest.revision: 15
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
# CHeapPtr Class
A smart pointer class for managing heap pointers.  
  
> [!IMPORTANT]
>  This class and its members cannot be used in applications that execute in the Windows Runtime.  
  
## Syntax  
  
```
template<
typename
T
,
class
Allocator
= CCRTAllocator
> class CHeapPtr :
public CHeapPtrBase<
T
,
Allocator
>
```  
  
#### Parameters  
 `T`  
 The object type to be stored on the heap.  
  
 `Allocator`  
 The memory allocation class to use.  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](../Topic/CHeapPtr::CHeapPtr.md)|The constructor.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CHeapPtr::Allocate](../Topic/CHeapPtr::Allocate.md)|Call this method to allocate memory on the heap to store objects.|  
|[CHeapPtr::Reallocate](../Topic/CHeapPtr::Reallocate.md)|Call this method to reallocate the memory on the heap.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[CHeapPtr::operator =](../Topic/CHeapPtr::operator%20=.md)|The assignment operator.|  
  
## Remarks  
 `CHeapPtr` is derived from [CHeapPtrBase](../atl/cheapptrbase-class.md) and by default uses the CRT routines (in [CCRTAllocator](../atl/ccrtallocator-class.md)) to allocate and free memory. The class [CHeapPtrList](../atl/cheapptrlist-class.md) may be used to construct a list of heap pointers. See also [CComHeapPtr](../atl/ccomheapptr-class.md), which uses COM memory allocation routines.  
  
## Inheritance Hierarchy  
 [CHeapPtrBase](../atl/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## Requirements  
 **Header:** atlcore.h  
  
##  <a name="cheapptr__allocate"></a>  CHeapPtr::Allocate  
 Call this method to allocate memory on the heap to store objects.  
  
```
bool Allocate(size_t
nElements  = 1) throw();
```  
  
### Parameters  
 `nElements`  
 The number of elements used to calculate the amount of memory to allocate. The default value is 1.  
  
### Return Value  
 Returns true if the memory was successfully allocated, false on failure.  
  
### Remarks  
 The allocator routines are used to reserve enough memory on the heap to store *nElement* objects of a type defined in the constructor.  
  
### Example  
 [!code[NVC_ATL_Utilities#77](../atl/codesnippet/CPP/cheapptr-class_1.cpp)]  
  
##  <a name="cheapptr__cheapptr"></a>  CHeapPtr::CHeapPtr  
 The constructor.  
  
```
CHeapPtr() throw();

explicit CHeapPtr(
    T*    p) throw();

CHeapPtr(
    CHeapPtr<T, Allocator>&   p) throw();
```  
  
### Parameters  
 `p`  
 An existing heap pointer or `CHeapPtr`.  
  
### Remarks  
 The heap pointer can optionally be created using an existing pointer, or a `CHeapPtr` object. If so, the new `CHeapPtr` object assumes responsibility for managing the new pointer and resources.  
  
### Example  
 [!code[NVC_ATL_Utilities#78](../atl/codesnippet/CPP/cheapptr-class_2.cpp)]  
  
##  <a name="cheapptr__operator__eq"></a>  CHeapPtr::operator =  
 Assignment operator.  
  
```
CHeapPtr<T,
    Allocator>&  operator=(
    CHeapPtr<T,
    Allocator>&   p) throw();
```  
  
### Parameters  
 `p`  
 An existing `CHeapPtr` object.  
  
### Return Value  
 Returns a reference to the updated `CHeapPtr`.  
  
### Example  
 [!code[NVC_ATL_Utilities#80](../atl/codesnippet/CPP/cheapptr-class_3.cpp)]  
  
##  <a name="cheapptr__reallocate"></a>  CHeapPtr::Reallocate  
 Call this method to reallocate the memory on the heap.  
  
```
bool Reallocate(size_t    nElements) throw();
```  
  
### Parameters  
 `nElements`  
 The new number of elements used to calculate the amount of memory to allocate.  
  
### Return Value  
 Returns true if the memory was successfully allocated, false on failure.  
  
### Example  
 [!code[NVC_ATL_Utilities#79](../atl/codesnippet/CPP/cheapptr-class_4.cpp)]  
  
## See Also  
 [CHeapPtrBase Class](../atl/cheapptrbase-class.md)   
 [CCRTAllocator Class](../atl/ccrtallocator-class.md)   
 [Class Overview](../atl/atl-class-overview.md)
