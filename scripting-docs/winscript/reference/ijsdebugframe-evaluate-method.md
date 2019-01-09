---
title: Метод IJsDebugFrame::Evaluate | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 574af7823add67a00fc8add922b5e352fa1b369c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091927"
---
# <a name="ijsdebugframeevaluate-method"></a>Метод IJsDebugFrame::Evaluate
Вычисление выражения в контексте этого кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExpressionText`  
 [in] Выражение для вычисления.  
  
 `ppDebugProperty`  
 [out] Объект, представляющий обозреватель свойств.  
  
 `pError`  
 [out] Сообщение об ошибке, если произошла ошибка.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает следующее: ЗНАЧЕНИЕ S_OK: Вычисление завершается успешно, * ppDebugProperty содержит результат вычисления. S_FALSE. Вычисление создает ошибку (или вычислительная операция не поддерживается), \*pError содержит сообщение об ошибке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)