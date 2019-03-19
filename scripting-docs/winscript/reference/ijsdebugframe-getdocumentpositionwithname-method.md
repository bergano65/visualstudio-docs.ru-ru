---
title: Метод IJsDebugFrame::GetDocumentPositionWithName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b909f3a3ebc672bf6d0a014b519de685b1677
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157312"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Метод IJsDebugFrame::GetDocumentPositionWithName
Возвращает текущее положение этого кадра стека в пределах пользовательского документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocumentName`  
 [out] Для статических скриптов URL-адрес документа. Для динамических скриптов возвращается имя, содержащее тип скрипта (например, код eval, код функции и т.д.).  
  
 `pLine`  
 [out] позиция строки на основе 1 в документе.  
  
 `pColumn`  
 [out] позиция строки на основе 1 в документе.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)