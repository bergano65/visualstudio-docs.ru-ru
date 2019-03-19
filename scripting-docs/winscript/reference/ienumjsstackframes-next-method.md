---
title: Метод IEnumJsStackFrames::Next | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94e3f478654fadec152aba0690a5474ebbfe02f5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159066"
---
# <a name="ienumjsstackframesnext-method"></a>Метод IEnumJsStackFrames::Next
Получает заданное число фрагментов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cFrameCount`  
 [in] Число кадров для получения.  
  
 `pFrames`  
 [out] Массив для хранения кадров.  
  
 `pcFetched`  
 [out] Количество возвращаемых кадров.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumJsStackFrames](../../winscript/reference/ienumjsstackframes-interface.md)