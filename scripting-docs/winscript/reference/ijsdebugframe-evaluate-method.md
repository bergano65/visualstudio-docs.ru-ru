---
title: "Метод IJsDebugFrame::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugFrame::Evaluate
Вычисляет выражение в контексте этого кадра стека.  
  
## Синтаксис  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### Параметры  
 `pExpressionText`  
 \[in\] Обрабатываемое выражение.  
  
 `ppDebugProperty`  
 \[out\] Объект, представляющий обозреватель свойств.  
  
 `pError`  
 \[out\] Сообщение об ошибке при возникновении ошибки.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает следующее: S\_ОК. Вычисление \*ppDebugProperty завершается успешно, содержащее результат вычислений.  S\_FALSE. Вычисление создает ошибку \(или операцию вычисления не поддерживает\), \*pError содержит сообщение об ошибке.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)