---
title: 'Иенумдебугстаккфрамес:: Next | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575548"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Извлекает указанное количество сегментов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 окне Число извлекаемых сегментов.  
  
 `prgdsfd`  
 заполняет Возвращает массив интерфейсов `DebugStackFrameDescriptor`, представляющих получаемые сегменты.  
  
 `pceltFetched`  
 заполняет Фактическое число сегментов, выбранных перечислителем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод извлекает указанное число сегментов в последовательности перечисления.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иенумдебугстаккфрамес](../../winscript/reference/ienumdebugstackframes-interface.md)  
 [Структура DebugStackFrameDescriptor](../../winscript/reference/debugstackframedescriptor-structure.md)