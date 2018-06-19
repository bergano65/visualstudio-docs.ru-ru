---
title: Функция Debug.msUpdateAsyncCallbackRelation | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636224"
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Функция Debug.msUpdateAsyncCallbackRelation
Обновляет состояние отношения между синхронным рабочим элементом и связанной с ним асинхронной операцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>Параметры  
 `relatedAsyncOperationId`  
 Обязательный. Идентификатор, связанный с асинхронной операцией.  
  
 `relationType`  
 Необязательно. Значение, задающее состояние отношения.  
  
## <a name="remarks"></a>Примечания  
 Синхронный рабочий элемент — это обычно функция обратного вызова для асинхронной операции. Эта функция может вызываться при прерывании асинхронной операции, использовании операции соединения и в других случаях.  
  
 Возможные значения параметра `relationType`:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Дополнительные сведения см. в разделе [константы отладки](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Некоторые средства отладки не отображают сведения, отправленные в отладчик этой функцией.  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]