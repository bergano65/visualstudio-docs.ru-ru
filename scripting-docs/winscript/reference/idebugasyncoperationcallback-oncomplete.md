---
title: IDebugAsyncOperationCallBack::onComplete | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4909f469b558ef4664a74c4a7926001d20adc40e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089405"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Сообщает, что результат доступен из операции асинхронной отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод сообщает, что результат доступен из `IDebugAsyncOperation` объекта. Это событие происходит в потоке отладчика.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugAsyncOperationCallBack](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)