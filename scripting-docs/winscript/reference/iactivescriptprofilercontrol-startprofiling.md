---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
При профилировании начинается на обработчике скриптов.  Обработчик скриптов создает экземпляр объекта профилировщика путем вызова [CoCreateInstance](http://msdn.microsoft.com/ru-ru/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## Синтаксис  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### Параметры  
 `clsidProfilerObject`  
 \[in\] идентификатор класса \(CLSID\) объекта профилировщика, которые необходимо создать.  
  
 `dwEventMask`  
 \[in\] значение битовой маски 4 байт, указывает типы событий.  Биты определены в [Перечисление PROFILER\_EVENT\_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 \[in\] а значение 4 байтов, которое передается в объект профилировщика.  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Профилирование уже включено.|  
  
## См. также  
 [Интерфейс IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)