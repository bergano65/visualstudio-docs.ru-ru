---
title: 'Идебугасинкоператион:: Start | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573244"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Вызывает запуск асинхронной операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `padocb`  
 Интерфейс обратного вызова, который получает события состояния от этой операции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_UNEXPECTED`|Операция уже находится в состоянии ожидания.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывает асинхронный вызов `IDebugSyncOperation::Execute` в потоке, полученном из `IDebugSyncOperation::GetTargetThread`. Этот метод должен вызываться только в потоке отладчика; в противном случае она не будет возвращаться до завершения операции.  
  
## <a name="see-also"></a>См. также  
 [Идебугасинкоператион:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)    
 @No__t_1 [интерфейса идебугасинкоператион](../../winscript/reference/idebugasyncoperation-interface.md)  
 [Идебугсинкоператион:: Execute](../../winscript/reference/idebugsyncoperation-execute.md)    
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)