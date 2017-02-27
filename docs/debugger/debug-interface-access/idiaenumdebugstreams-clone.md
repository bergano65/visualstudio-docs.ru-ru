---
title: "IDiaEnumDebugStreams::Clone | Microsoft Docs"
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
  - "IDiaEnumDebugStreams::Clone - метод"
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumDebugStreams::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### Параметры  
 `ppenum`  
 \[out\] возвращает [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) объект, содержащий дубликат перечислителя.  Потоки не скопированы только перечислитель.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)