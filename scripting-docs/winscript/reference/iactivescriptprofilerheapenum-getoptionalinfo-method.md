---
title: Метод IActiveScriptProfilerHeapEnum::GetOptionalInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcba1214a0c57e738dec41cdc4976f478802fedc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088807"
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