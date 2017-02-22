---
title: "CV_access_e | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_access_e - перечисление"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Определяет область видимости \(уровень доступа\) функций\-членов и переменных.  
  
## Синтаксис  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elements  
 CV\_private  
 Элемент имеет закрытый доступ.  
  
 CV\_protected  
 Элемент защищал доступ.  
  
 CV\_public  
 Член, имеющий открытый доступ.  
  
## Заметки  
 `friend` описатель доступа не включен здесь, поскольку обычно используется функциями non\-участника, имеющих доступ к закрытым и защищенным элементам и класса.  Используйте [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) метод, чтобы найти символы с  `SymTagFriend` доступ.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)