---
title: "Compiler Error C3389"
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
  - "C3389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3389"
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 9
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
# Compiler Error C3389
__declspec(keyword) cannot be used with /clr:pure or /clr:safe  
  
 A [__declspec](../cpp/__declspec.md) modifier used implies a per process state.  [/clr:pure](../buildref/-clr--common-language-runtime-compilation-.md) implies a per [appdomain](../cpp/appdomain.md) state.  So, declaring a variable with the `keyword`**__declspec** modifier and compiling with **/clr:pure** is not allowed.  
  
 The following sample generates C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```