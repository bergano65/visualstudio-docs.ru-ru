---
title: "IDiaInjectedSource::get_objectFilename | Microsoft Docs"
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
  - "IDiaInjectedSource::get_objectFilename - метод"
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_objectFilename
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает имя файла объекта, на который был источником компилирования.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_objectFilename (   
   BSTR* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает имя файла источника объекта, к которому был компилироваться.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)