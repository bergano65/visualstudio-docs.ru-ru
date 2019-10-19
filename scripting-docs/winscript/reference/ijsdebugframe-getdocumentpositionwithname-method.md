---
title: 'Метод метод ijsdebugframe:: Жетдокументпоситионвиснаме | Документация Майкрософт'
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
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575123"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>Метод IJsDebugFrame::GetDocumentPositionWithName
Возвращает текущую координату этого кадра стека в документе уровня пользователя.  
  
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
 заполняет Для статических скриптов — URL-адрес документа. Для динамических скриптов возвращается имя, содержащее тип скрипта (например, код eval, код функции и т. д.).  
  
 `pLine`  
 [out] 1-разрядная строка в документе.  
  
 `pColumn`  
 [out] 1-разрядная строка в документе.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)