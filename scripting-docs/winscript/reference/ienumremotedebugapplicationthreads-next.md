---
title: IEnumRemoteDebugApplicationThreads::Next | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b2aaa1882b5699343d82ecae5fe236574802d7d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092395"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
`Next` Метод извлекает указанное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество сегментов для получения.  
  
 `pprdat`  
 [out] Возвращает массив `IRemoteDebugApplicationThread` интерфейсы, которые представляет сегменты, которые требуется получить.  
  
 `pceltFetched`  
 [out] Фактическое число сегментов, получены с помощью перечислителя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод извлекает указанное число сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)