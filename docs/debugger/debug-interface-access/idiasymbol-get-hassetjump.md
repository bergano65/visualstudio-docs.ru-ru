---
title: "IDiaSymbol::get_hasSetJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSetJump - метод"
ms.assetid: 22656206-dccf-40ed-b179-fc016d1b262a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_hasSetJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, содержит ли функция использование [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) команда \(с связыванная  [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) команда эти формы метода в стиле обработки ошибок\).  
  
## Синтаксис  
  
```cpp  
HRESULT get_hasSetJump(  
   BOOL *pFlag  
);  
```  
  
#### Параметры  
 `pFlag`  
 \[out\] возвращает `TRUE` если функция содержит a  `setjmp` команда; в противном случае возвращает  `FALSE`.  
  
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
 [IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)