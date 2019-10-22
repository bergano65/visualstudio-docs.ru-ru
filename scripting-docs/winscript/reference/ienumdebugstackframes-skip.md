---
title: 'Иенумдебугстаккфрамес:: Skip | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29e5864d1304aeb4c916e93da8b151336596d979
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575541"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
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
 [Интерфейс IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)