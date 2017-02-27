---
title: "IDiaFrameData::get_type | Microsoft Docs"
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
  - "IDiaFrameData::get_type - метод"
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает тип кадра компилятор\-специфического.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает значение [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) перечисление, указывающее тип кадра компилятор\-специфического.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)