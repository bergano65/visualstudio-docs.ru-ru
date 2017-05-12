---
title: "Функция Debug.msUpdateAsyncCallbackRelation | Microsoft Docs"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция Debug.msUpdateAsyncCallbackRelation
Обновляет состояние отношения между синхронным рабочим элементом и связанной с ним асинхронной операцией.  
  
## Синтаксис  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### Параметры  
 `relatedAsyncOperationId`  
 Обязательный.  Идентификатор, связанный с асинхронной операцией.  
  
 `relationType`  
 Необязательно.  Значение, задающее состояние отношения.  
  
## Заметки  
 Синхронный рабочий элемент — это обычно функция обратного вызова для асинхронной операции.  Эта функция может вызываться при прерывании асинхронной операции, использовании операции соединения и в других случаях.  
  
 Возможные значения параметра `relationType`:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Дополнительные сведения см. в разделе [Константы отладки](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Некоторые средства отладки не отображают сведения, отправленные в отладчик этой функцией.  
  
## Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]