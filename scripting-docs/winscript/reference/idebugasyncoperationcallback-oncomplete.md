---
title: 'Идебугасинкоператионкаллбакк:: OnComplete | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573240"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Сообщает о том, что результат доступен при асинхронной операции отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод сигнализирует, что результат доступен из объекта `IDebugAsyncOperation`. Событие срабатывает в потоке отладчика.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугасинкоператионкаллбакк](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)