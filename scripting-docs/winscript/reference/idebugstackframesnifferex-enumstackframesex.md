---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727584"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Возвращает перечислитель кадров стека текущего потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSpMin`  
 [in] Нижняя граница адрес для перечисления кадры стека.  
  
 `ppedsf`  
 [out] Перечислитель кадров стека текущего потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Возвращает перечислитель кадра стека кадры, начиная с верхней части стека с наиболее недавно отправленных кадра. Перечислитель содержит только кадры стека с адресами больше или равно `dwSpMin`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)