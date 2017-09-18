---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает идентификатор GUID для всех возможных обработчиков отладки \(DE\), которые могут отлаживать этой программы.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### Параметры  
 `celtBuffer`  
 \[in\] число DE GUID, который необходимо вернуть.  Это также определяет максимальный размер `rgguidEngines` массив.  
  
 `rgguidEngines`  
 \[in, out\] массив DE GUID, который требуется заполнить.  
  
 `pceltEngines`  
 \[out\] возвращает фактический номер DE GUID, которое возвращается.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает \[C\+\+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` or \[c\#\] 0x8007007A если буфер недостаточно велик.  
  
## Заметки  
 Чтобы определить, сколько обработчиков существует, этот метод вызывается один раз с `celtBuffer` имеет значение 0, а параметр  `rgguidEngines` набор параметров в значение NULL.  Возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(для c\#\) и 0x8007007A  `pceltEngines` параметр возвращает необходимый размер буфера.  
  
## См. также  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)