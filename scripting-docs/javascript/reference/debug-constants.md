---
title: "Константы отладки | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Константы отладки
Константы отладки возвращают постоянные значения, являющиеся свойствами объекта `Debug`.  
  
## Константы объекта Debug  
 В следующей таблице перечислены значения констант, являющиеся свойствами [объекта Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Константа|Описание|Значение|  
|---------------|--------------|--------------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|Синхронный рабочий элемент назначил обратный вызов или продолжение для выполнения асинхронной операцией.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|Синхронный рабочий элемент удовлетворил часть асинхронной операции присоединения.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|Синхронный рабочий элемент удовлетворил асинхронную операцию выбора.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|Синхронный рабочий элемент был отменен.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|Синхронный рабочий элемент вызвал ошибку в асинхронной операции.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Асинхронная операция была выполнена успешно.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Асинхронная операция была отменена.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|Асинхронная операция привела к ошибке.|3|  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## См. также  
 [Функция Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Функция Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)