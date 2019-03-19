---
title: Интерфейс IActiveScriptProfilerHeapEnum | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe83f00a96013ffcf7c5df2d47eb1ba7d7a0bae1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144918"
---
# <a name="iactivescriptprofilerheapenum-interface"></a>Интерфейс IActiveScriptProfilerHeapEnum
Итератор, указывающий над данной кучей объектов, связанных с механизмом скриптов, собранные [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## <a name="methods"></a>Методы  
 [Метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Получает следующий объект или объекты в наборе объектов кучи, собранные [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Получает Дополнительные сведения для заданного объекта в наборе объектов кучи, собранные [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [Метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Освобождает указанный [структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) структур и связанные с ними [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) элементов.  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Возвращает имена строки, соответствующих [тип PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md) значения...