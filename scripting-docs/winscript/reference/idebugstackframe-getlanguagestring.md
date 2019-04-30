---
title: IDebugStackFrame::GetLanguageString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab0c0ab317754305ca2440748dd680e31750d8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934666"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Возвращает короткое или долго текстовое описание языка.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fLong`  
 [in] Флаг, где `TRUE` возвращает подробное описание и `FALSE` возвращает краткое описание.  
  
 `pbstrLanguage`  
 [out] Описание языка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Как правило если `fLong` является `FALSE`, этот метод предоставляет только имя языка, связанного с этим кадром стека. Когда `fLong` является `TRUE`, этот метод может предоставить описание полной версии продукта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)