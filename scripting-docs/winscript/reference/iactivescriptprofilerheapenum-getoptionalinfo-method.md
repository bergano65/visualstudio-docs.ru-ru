---
title: "Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo
Получает Дополнительные сведения в указанном объекте (из набора объектов кучи, возвращенных [метод IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Не должен освободить возвращаемый память, назначенная возвращаемых объектов. Вместо этого следует вызвать метод [метод IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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