---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
Задает битовую маску 4 байт, указывает типы событий, должно вызываться событие обработчика сценариев.  
  
## Синтаксис  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### Параметры  
 `dwEventMask`  
 \[in\] значение битовой маски 4 байт, указывает типы событий.  Биты определены в [Перечисление PROFILER\_EVENT\_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Профилирование не включено.|  
  
## См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)