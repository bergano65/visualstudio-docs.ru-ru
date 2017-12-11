---
title: "Функция JsEnumerateHeap | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsEnumerateHeap
helpviewer_keywords: JsEnumerateHeap function
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48d7698218df49b8ffd680cf26df370c2f97b7c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsenumerateheap-function"></a>Функция JsEnumerateHeap
Выполняет перечисление кучи в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `enumerator`  
 Перечислитель кучи.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 При перечислении кучи текущий контекст не может быть удален, и все вызовы для изменения состояния контекста будут завершаться ошибкой до тех пор, пока перечислитель кучи не будет освобожден.  
  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается в настольных приложениях, но не поддерживается в приложениях Магазина.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)