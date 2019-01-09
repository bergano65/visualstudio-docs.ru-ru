---
title: Метод IActiveScriptProfilerControl5::EnumHeap2 | Документация Майкрософт
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
ms.openlocfilehash: 21661953edbdba2314b88aad5fb55451b06b51a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097634"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>Метод IActiveScriptProfilerControl5::EnumHeap2
Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), можно использовать для итерации объектами кучи GC в контексте связанного обработчика скриптов.  
  
 Можно вызвать этот метод в любом отладки или в режиме выпуска. Этот метод должен вызываться, когда поток пользовательского интерфейса неактивен. После вызова метода для обработчика сценариев, за исключением выполняться никакие операции [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) пока [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)возвращает значение S_FALSE или [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) будет освобожден указатель интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Параметры  
 enumFlags  
 Значение, указывающее, предоставляется ли дополнительная информацию об объект, на который указывает указатель в объектном отношении. Дополнительные сведения могут указывать, является ли объект, на который указывает метод доступа get или Set. Дополнительные сведения см. в разделе [перечисление PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Возвращает [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение HRESULT. Ниже приведены возможные значения.  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Перечисление кучи успешно завершена.|  
|`E_OUTOFMEMORY`|Недостаточно памяти для выполнения перечисления кучи не существует.|  
|`E_FAIL`|Произошла внутренняя ошибка.|