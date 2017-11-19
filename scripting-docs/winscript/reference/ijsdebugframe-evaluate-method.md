---
title: "Метод IJsDebugFrame::Evaluate | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframeevaluate-method"></a>Метод IJsDebugFrame::Evaluate
Вычисление выражения в контексте данного кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [out] Объект, представляющий свойства браузера.  
  
 `pError`  
 [out] Сообщение об ошибке, если произошла ошибка.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает следующее: значение S_OK: прохождения проверки, * ppDebugProperty содержит результат вычисления. S_FALSE: Оценки вызывает ошибку (или вычислительная операция не поддерживается), \*pError содержит сообщение об ошибке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)