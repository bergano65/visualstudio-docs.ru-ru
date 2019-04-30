---
title: Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992842"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo
Получает Дополнительные сведения в указанном объекте (из набора объектов кучи, возвращенные [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Не следует освободить возвращаемый памяти, назначенной возвращаемых объектов. Вместо этого следует вызывать [метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Параметры  
 `heapObject`  
 [Структура PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) для которого возвращаются сведения.  
  
 `celt`  
 Число [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) структур для возврата.  
  
 `optionalInfo`  
 [out] Массив [структура PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) структур для указанного объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT.