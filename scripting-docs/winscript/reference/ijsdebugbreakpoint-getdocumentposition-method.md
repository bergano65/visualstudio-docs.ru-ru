---
title: "Метод IJsDebugBreakPoint::GetDocumentPosition | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c33751b0173626814f042fdc54a7d496b644573
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Метод IJsDebugBreakPoint::GetDocumentPosition
Возвращает позицию инструкции связыванием точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocumentId`  
 [out] Уникальный идентификатор для исходного документа (указатель на IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] Отсчитываемый от нуля смещение от начала скрипта.  
  
 `pStatementCharCount`  
 [out] Длина текущего инструкцию, которая начинается с * pCharacterOffset в символах.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)