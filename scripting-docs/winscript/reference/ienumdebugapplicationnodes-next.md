---
title: IEnumDebugApplicationNodes::Next | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07bdd008887676ef2f4cba7e1a67d96e1344f56a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091134"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Возвращает указанное количество сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество сегментов для получения.  
  
 `pprddp`  
 [out] Возвращает массив `IDebugApplicationNode` интерфейсы, которые представляет сегменты, которые требуется получить.  
  
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
 [Интерфейс IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)