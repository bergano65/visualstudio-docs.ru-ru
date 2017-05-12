---
title: "IEnumRemoteDebugApplications::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Next"
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Next
Метод `Next` извлекает заданное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число сегментов, который необходимо извлечь.  
  
 `ppda`  
 \[out\] возвращает массив интерфейсов `IRemoteDebugApplication`, представляющий восстанавливаемая сегменты.  
  
 `pceltFetched`  
 \[out\] фактическое количество сегментов выбирается перечислителем.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод извлекает заданное количество сегментов в последовательности перечисления.  
  
## См. также  
 [Интерфейс IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)