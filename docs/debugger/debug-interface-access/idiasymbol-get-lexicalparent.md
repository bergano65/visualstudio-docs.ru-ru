---
title: "IDiaSymbol::get_lexicalParent | Microsoft Docs"
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
  - "IDiaSymbol::get_lexicalParent - метод"
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает ссылку на родительский словарному символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий родительский лексический символов.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение  `S_FALSE` означает, что свойство недоступно для символа.  
  
## Заметки  
 Лексический родительский символов включающего функции или модуля.  Например, лексический родительский параметра или локальной переменной функции сама функция пока лексический родительский функции модуля он определен.  
  
 Допустимые символы, которые могут отображаться как лексических документированы в родительские элементы [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)