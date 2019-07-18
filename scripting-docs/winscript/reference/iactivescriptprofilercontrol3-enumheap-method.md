---
title: Метод IActiveScriptProfilerControl3::EnumHeap | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6120b8fdd913b4acee2e3ee6774d770aa75b1f5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992966"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Метод IActiveScriptProfilerControl3::EnumHeap
Возвращает интерфейс ([интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), можно использовать для итерации объектами кучи GC в контексте связанного обработчика скриптов.  
  
 Можно вызвать этот метод в любом отладки или в режиме выпуска. Этот метод должен вызываться, когда поток пользовательского интерфейса неактивен. После вызова метода для обработчика сценариев, за исключением выполняться никакие операции [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) пока [метод IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)возвращает значение S_FALSE или [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) будет освобожден указатель интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Параметры  
 ppEnum  
 [out] Возвращает [интерфейс IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT.