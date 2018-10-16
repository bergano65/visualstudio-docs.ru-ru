---
title: Метод IActiveScriptProfilerControl5::EnumHeap2 | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724664"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>Метод IActiveScriptProfilerControl5::EnumHeap2
Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) может использоваться для перебора объектов кучи сборщика Мусора в контексте обработчика связанных сценариев.  
  
 Можно вызвать этот метод в любом отладки или в режиме выпуска. Этот метод должен вызываться во время простоя потока пользовательского интерфейса. После вызова метода, необходимо выполнить никакие операции в обработчик сценариев, за исключением [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) до [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)возвращает значение S_FALSE или [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) освобождается указатель на интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Параметры  
 enumFlags  
 Значение, указывающее, предоставляется ли Дополнительные сведения об объекте, на который указывает в отношении объекта. Дополнительных сведений может указывать, является ли объект, на который указывает метод доступа get или Set. Дополнительные сведения см. в разделе [перечисление PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Возвращает [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Перечисление кучи успешно завершена.|  
|`E_OUTOFMEMORY`|Не хватает памяти для выполнения перечисление кучи.|  
|`E_FAIL`|Произошла внутренняя ошибка.|