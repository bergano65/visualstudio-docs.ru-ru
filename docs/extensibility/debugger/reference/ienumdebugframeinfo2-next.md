---
title: "IEnumDebugFrameInfo2::Next | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bd30e1b33030d72083eb3046e22368cdd665654d
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG       celt,  
   FRAMEINFO** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint        celt,  
   FRAMEINFO[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число элементов для извлечения. Также определяет максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [in, out] Массив [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) элементы, которые должны заполняться в.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически извлеченных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше запрошенного количества элементов может быть возвращен; в противном случае — возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
