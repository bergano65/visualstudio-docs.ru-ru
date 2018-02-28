---
title: "IDebugApplicationThread::SynchronousCallIntoThread | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdeb57380975f19424f8b7da783846b5aae976ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Предоставляет механизм для вызывающего объекта запустить код в потоке приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstcb`  
 [in] Объект для вызова.  
  
 `dwParam1`  
 [in] Первый параметр для передачи `IDebugThreadCall::ThreadCallHandler` метод.  
  
 `dwParam2`  
 [in] Второй параметр для передачи `IDebugThreadCall::ThreadCallHandler` метод.  
  
 `dwParam3`  
 [in] Третий параметр для передачи `IDebugThreadCall::ThreadCallHandler` метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод предоставляет механизм для вызывающего объекта, для выполнения кода в поток отладки. Модули языка и узлы обычно используется этот метод для реализации свободнопоточный объекты на основе реализаций одного однопотоковое.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)