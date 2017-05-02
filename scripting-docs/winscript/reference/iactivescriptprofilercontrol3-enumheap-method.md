---
title: "Метод IActiveScriptProfilerControl3::EnumHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Метод IActiveScriptProfilerControl3::EnumHeap
Возвращает интерфейс \([Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\), который может использоваться для перебора объектов кучи сборки мусора в контексте связанного обработчика скриптов.  
  
 Этот метод можно вызывать в режим отладки или освобождаете.  Этот метод должен быть вызван, когда поток пользовательского интерфейса в состоянии бездействия.  После того, как был вызван метод, не следует выполнять никаких операций для обработчика скрипта, за исключением [IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) до тех пор, пока [IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) возвращает значение S\_FALSE или указатель интерфейса [Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) освободить.  
  
## Синтаксис  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Параметры  
 ppEnum  
 \[out\] Возвращает [Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Возвращаемое значение  
 HRESULT.