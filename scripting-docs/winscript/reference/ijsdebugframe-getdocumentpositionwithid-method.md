---
title: Метод IJsDebugFrame::GetDocumentPositionWithId | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4c37f31ca6b75ca826dbdab93847a1e70ff054c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090016"
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