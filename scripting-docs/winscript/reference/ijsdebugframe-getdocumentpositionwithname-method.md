---
title: "Метод IJsDebugFrame::GetDocumentPositionWithName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Метод IJsDebugFrame::GetDocumentPositionWithName
Возвращает текущую позицию этого кадра стека в документе уровня пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocumentName`  
 [out] Для статических сценариев URL-адрес документа. Для динамических сценариев возвращается имя, содержащее тип сценария (например, eval код, код функции и т.д.).  
  
 `pLine`  
 [out] строки на основе 1 позиции в документе.  
  
 `pColumn`  
 [out] строки на основе 1 позиции в документе.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)