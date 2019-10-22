---
title: 'Метод метод ijsdebugframe:: Evaluate | Документация Майкрософт'
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573496"
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
 окне Вычисляемое выражение.  
  
 `ppDebugProperty`  
 заполняет Объект, представляющий обозреватель свойств.  
  
 `pError`  
 заполняет Сообщение об ошибке при возникновении ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает следующее: S_OK: Оценка выполнена, * Ппдебугпроперти содержит результат оценки. S_FALSE: при вычислении возникает ошибка (или операция вычисления не поддерживается), \*pError содержит сообщение об ошибке.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)