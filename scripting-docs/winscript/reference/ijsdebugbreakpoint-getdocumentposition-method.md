---
title: Метод IJsDebugBreakPoint::GetDocumentPosition | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146eb26c887cd24d1eb7af858535fcecac62b41d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583149"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Метод IJsDebugBreakPoint::GetDocumentPosition
Возвращает позицию инструкции, где была привязана точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [out] Длина текущей инструкции, которая начинается с * pCharacterOffset, в символах.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)