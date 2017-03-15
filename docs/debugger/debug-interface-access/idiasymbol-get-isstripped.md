---
title: "IDiaSymbol::get_isStripped | Microsoft Docs"
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
  - "IDiaSymbol::get_isStripped - метод"
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_isStripped
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить указывающее, были ли закрытые символы удаляются из файлов символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_isStripped(  
   BOOL *pFlag  
);  
```  
  
#### Параметры  
 `pFlag`  
 \[out\] возвращает `TRUE` если закрытые символы удалены из файлов символов; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Это свойство доступно из `SymTagExe` тип символа \(см.  [Exe](../../debugger/debug-interface-access/exe.md)\).  
  
## Требования  
  
|Требование|Описание|  
|----------------|--------------|  
|Заголовок:|dia2.h|  
|Версия:|Пакет SDK для доступа к интерфейсу отладки v8.0|  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)