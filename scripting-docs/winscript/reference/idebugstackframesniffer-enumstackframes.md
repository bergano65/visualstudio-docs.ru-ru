---
title: "IDebugStackFrameSniffer::EnumStackFrames | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrameSniffer.EnumStackFrames
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrameSniffer::EnumStackFrames
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d64d896dcc14a280a74f64f5093b6708a7fcb5f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferenumstackframes"></a>IDebugStackFrameSniffer::EnumStackFrames
Возвращает перечислитель кадров стека текущего потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppedsf`  
 [out] Перечислитель кадров стека текущего потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Перечислитель кадра стека возвращает кадры, начиная с верхней части стека, начиная с наиболее недавно занесенный в стек.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)