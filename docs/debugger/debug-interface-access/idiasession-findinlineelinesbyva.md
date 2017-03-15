---
title: "IDiaSession::findInlineeLinesByVA | Microsoft Docs"
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает перечисление, которое позволяет клиенту выполнять перебор число линии всех функций, является встроенной, прямо или косвенно, указанным родительским символом и содержится в указанный виртуальный адрес \(VA\).  
  
## Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,  
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Параметры  
 `parent`  
 \[in\] объект `IDiaSymbol`, представляющий родительский элемент.  
  
 `va`  
 \[in\] задает адрес, как VA.  
  
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