---
title: "Метод IActiveScriptProfilerControl5::EnumHeap2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IActiveScriptProfilerControl5::EnumHeap2
Возвращает интерфейс \([Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\), который можно использовать для итерации объектами кучи СБОРКИ в контексте связанного обработчика скриптов.  
  
 Этот метод можно вызвать в режиме отладки или выпуска.  Этот метод должен вызываться, когда поток пользовательского интерфейса неактивен.  После того как метод был вызван, с обработчиком скриптов не должно выполняться никаких операций, кроме [IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md), до тех пор, пока [IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) не возвратит значение S\_FALSE или не будет освобожден указатель интерфейса [Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Синтаксис  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Параметры  
 enumFlags  
 Значение, указывающее, предоставляется ли дополнительная информацию об объекте кучи, на который указывает указатель в объектном отношении.  Дополнительные сведения могут указывать, что представляет собой объект, на который указывает указатель — метод get или метод set.  Дополнительные сведения см. в разделе [Перечисление PROFILER\_HEAP\_ENUM\_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 \[out\] Возвращает [Интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Возвращаемое значение  
 Возвращает значение HRESULT.  Ниже приведены возможные значения:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Перечисление кучи завершенные успешно.|  
|`E_OUTOFMEMORY`|Была не хватает памяти, доступной выполнить перечисление кучи.|  
|`E_FAIL`|Внутренняя ошибка.|