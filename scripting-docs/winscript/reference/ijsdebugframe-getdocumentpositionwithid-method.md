---
title: Метод IJsDebugFrame::GetDocumentPositionWithId | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741fe323e787c57f5f05a25461eae87c98dba70f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558142"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>Метод IJsDebugFrame::GetDocumentPositionWithId
Возвращает текущее положение этого кадра стека в пределах пользовательского документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentPositionWithId(  
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
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)