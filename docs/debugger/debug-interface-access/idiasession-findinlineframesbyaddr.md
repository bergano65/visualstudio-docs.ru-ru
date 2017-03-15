---
title: "IDiaSession::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает перечисление, которое позволяет клиенту выполнять перебор всех кадров встроенного по заданному адресу.  
  
## Синтаксис  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,  
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Параметры  
 `parent`  
 \[in\] объект `IDiaSymbol`, представляющий родительский элемент.  
  
 `isect`  
 \[in\] задает компонент раздела адреса.  
  
 `offset`  
 \[in\] задает компонент смещения адреса.  
  
 `ppResult`  
 \[out\] хранит объект `IDiaEnumSymbols`, содержащий список кадров, которые получены.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)