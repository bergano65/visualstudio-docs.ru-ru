---
title: "IDiaSymbol::get_hasLongJump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_hasLongJump - метод"
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, содержит ли функция использование [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) команда \(связыванная with a  [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) команда эти формы метода в стиле обработки ошибок\).  
  
## Синтаксис  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### Параметры  
 `pFlag`  
 \[out\] возвращает `TRUE` если функция содержит a  `longjmp` команда; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v8.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)