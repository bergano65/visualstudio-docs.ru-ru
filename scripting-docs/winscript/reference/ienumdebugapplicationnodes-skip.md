---
title: 'Иенумдебугаппликатионнодес:: Skip | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Skip
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Skip
ms.assetid: b2ad1957-95b5-4c09-9a44-5a765a5308ae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: def20df8ee38763856fb33d6410788c934f541a5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573021"
---
# <a name="ienumdebugapplicationnodesskip"></a>IEnumDebugApplicationNodes::Skip
Пропускает указанное число сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 окне Количество сегментов в последовательности перечисления, которые необходимо пропустить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод пропускает указанное число сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)