---
title: "Метод IActiveScriptProfilerControl3::EnumHeap | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Метод IActiveScriptProfilerControl3::EnumHeap
Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) может использоваться для перебора объектов кучи сборщика Мусора в контексте обработчика связанных сценариев.  
  
 Можно вызвать этот метод в любом отладки или в режиме выпуска. Этот метод должен вызываться во время простоя потока пользовательского интерфейса. После вызова метода, необходимо выполнить никакие операции в обработчик сценариев, за исключением [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) до [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)возвращает значение S_FALSE или [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) освобождается указатель на интерфейс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppEnum  
 [out] Возвращает [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT.