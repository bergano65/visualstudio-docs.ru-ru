---
title: "IDiaSession::findInlineeLinesByAddr | Microsoft Docs"
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
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом и содержится в указанный диапазон адресов.  
  
## Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,  
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Параметры  
 `parent`  
 \[in\] объект `IDiaSymbol`, представляющий родительский элемент.  
  
 `isect`  
 \[in\] задает компонент раздела адреса.  
  
 `offset`  
 \[in\] задает компонент смещения адреса.  
  
 `length`  
 \[in\] определяет диапазон адресов, число байт, чтобы предусматривать с данным запросом.  
  
 `ppResult`  
 \[out\] хранит объект `IDiaEnumLineNumbers`, который содержит список номеров линии, которые получены.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)