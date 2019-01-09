---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Документация Майкрософт
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
ms.openlocfilehash: 8c34ce267113ae5576a8b3bdca9ac34d4abc00f7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086975"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Возвращает перечислитель для кадров стека текущего потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSpMin`  
 [in] Нижняя граница адрес для перечисления кадров стека.  
  
 `ppedsf`  
 [out] Перечислитель для кадров стека текущего потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Возвращает перечислитель кадра стека кадры, начиная с верхней части стека, с наиболее недавно отправленных кадром. Перечислитель содержит только кадры стека с адресами больше или равно `dwSpMin`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)