---
title: "ComPtr::operator Microsoft::WRL::Details::BoolType Operator"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
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
# ComPtr::operator Microsoft::WRL::Details::BoolType Operator
Indicates whether or not a ComPtr is managing the object lifetime of an interface.  
  
## Syntax  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## Return Value  
 If an interface is associated with this ComPtr, the address of the [BoolStruct::Member](../windows/boolstruct--member-data-member.md) data member; otherwise, `nullptr`.  
  
## Requirements  
 **Header:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## See Also  
 [ComPtr Class](../windows/comptr-class.md)   
 [ComPtr::Get Method](../windows/comptr--get-method.md)