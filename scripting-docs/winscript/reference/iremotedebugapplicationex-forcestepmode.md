---
title: "IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:ForceStepMode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:ForceStepMode"
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:ForceStepMode
Вызывает отладчик в режим единый\- шага.  
  
## Синтаксис  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### Параметры  
 `pStepThread`  
 \[in\] поток монитора для отладки процесса, который необходимо выполнить.  Если значение равно null, PDM очищает его поток пошаговое выполнение.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/ru-ru/2f65fa67-06b7-4053-8945-22383ab66343)