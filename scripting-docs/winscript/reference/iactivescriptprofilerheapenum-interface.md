---
title: "Интерфейс IActiveScriptProfilerHeapEnum | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Интерфейс IActiveScriptProfilerHeapEnum
Итератор над объектами кучи, связанные с обработчиком скрипта, собранный [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Синтаксис  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## Методы  
 [IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Возвращает следующий объект или объекты в наборе объектов кучи, полученных [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Возвращает дополнительные сведения об указанном объекте в наборе объектов кучи, полученных [Метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Освобождает [Структура PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) указанные структуры и связанные с ними элементы [Структура PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Возвращает имена строки, соответствующие значениям [Тип PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md).