---
title: "IDiaSymbol::get_compilerName | Microsoft Docs"
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
  - "IDiaSymbol::get_compilerName - метод"
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_compilerName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает имя компилятора, используемого для формирования [Compiland](../../debugger/debug-interface-access/compiland.md).  
  
## Синтаксис  
  
```cpp#  
HRESULT get_compilerName (  
   BSTR *pName  
);  
```  
  
#### Параметры  
 `pName`  
 Указатель на строку BSTR, которое будет содержать имя в юникоде компилятора.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v8.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)