---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
Вызываемый для инициализации объект профилировщика при профилирующ начавшийся в обработчике скриптов.  
  
## Синтаксис  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### Параметры  
 `dwContext`  
 \[in\] а значение 4 байтов, которое передается [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Если методу не удается инициализировать объект профилировщика, он должен возвратить сбой HRESULT уведомление обработчика скриптов.  В этом случае обработчик скриптов должен напрямую вызывать [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), указав значение HRESULT в параметре, а затем освобождает объект профилировщика.  
  
## См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)