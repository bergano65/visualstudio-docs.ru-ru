---
title: "IEnumRemoteDebugApplicationThreads::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Clone"
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Clone
Создает перечислитель с тем же состоянием, что и текущий перечислитель.  
  
## Синтаксис  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### Параметры  
 `pperdat`  
 \[out\] возвращает интерфейс `IEnumRemoteDebugApplicationThreads` клона перечислителя.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод создает перечислитель с тем же состоянием как текущий перечислитель.  
  
## См. также  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)