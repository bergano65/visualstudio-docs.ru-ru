---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает все значения тега указателя сочетаний клавиш, которые соответствуют функции заглушки сочетаний клавиш C\+\+ AMP.  
  
## Синтаксис  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Параметры  
 `cnt`  
 \[in\] размер массива `pPointerTags` вывода.  
  
 `pcnt`  
 \[out\] количество тегов указателя сочетаний клавиш в функции заглушки сочетаний клавиш C\+\+ AMP.  
  
 `pPointerTags`  
 \[out\] указатель массива a `DWORD`, который заполняется тегом указателя сочетаний клавиш оценивает в функции заглушки сочетаний клавиш C\+\+ AMP.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## Заметки  
 Этот метод вызывается в интерфейсе `IDiaSymbol`, который соответствует функции заглушки сочетаний клавиш C\+\+ AMP.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)