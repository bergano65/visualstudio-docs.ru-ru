---
title: Метод IJsDebugFrame::Evaluate | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157819"
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
 Возвращает следующее: ЗНАЧЕНИЕ S_OK: Вычисление завершается успешно, * ppDebugProperty содержит результат вычисления. S_FALSE: Вычисление создает ошибку (или вычислительная операция не поддерживается), \*pError содержит сообщение об ошибке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)