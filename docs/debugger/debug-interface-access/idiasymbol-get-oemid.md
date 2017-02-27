---
title: "IDiaSymbol::get_oemId | Microsoft Docs"
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
  - "IDiaSymbol::get_oemId - метод"
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_oemId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает значение идентификатора нестандартных производителя оборудования \(OEM\) символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_oemId (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает уникальное значение, указывающее OEM.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Это свойство применяется только к символам with a [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) тип   `SymTagCustomType`.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)