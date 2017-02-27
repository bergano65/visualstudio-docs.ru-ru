---
title: "IDiaEnumDebugStreams::Next | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Next - метод"
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreams::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает заданное количество потоков в последовательности перечисления отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG                     celt,   
   IDiaEnumDebugStreamData** rgelt,  
   ULONG*                    pceltFetched  
);  
```  
  
#### Параметры  
 celt  
 \[in\] **Т**он номер отладки потоки в перечислителе.  
  
 rgelt  
 \[out\] возвращает массив [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) объекты, представляющее восстанавливаемая потоки отладки.  
  
 pceltFetched  
 \[out\] возвращает число debug, возвращенные потоками.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если несколько потоков.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)