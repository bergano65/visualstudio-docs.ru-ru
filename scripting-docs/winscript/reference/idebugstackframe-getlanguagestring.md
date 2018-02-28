---
title: "IDebugStackFrame::GetLanguageString | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724ca98278eb8885d29aad1799f822ac57251597
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Возвращает короткое или долго текстовое описание языка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 Как правило если `fLong` — `FALSE`, этот метод предоставляет только имя языка, связанного с этим кадром стека. Когда `fLong` — `TRUE`, этот метод может предоставить описание полной версии продукта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)