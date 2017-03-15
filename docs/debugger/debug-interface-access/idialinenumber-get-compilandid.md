---
title: "IDiaLineNumber::get_compilandId | Microsoft Docs"
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
  - "IDiaLineNumber::get_compilandId - метод"
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_compilandId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает уникальный идентификатор для compiland, использованное эту линию.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `DWORD` содержит уникальный идентификатор compiland, использованное эту линию.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)