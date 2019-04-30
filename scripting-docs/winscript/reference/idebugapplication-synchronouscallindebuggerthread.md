---
title: IDebugApplication::SynchronousCallInDebuggerThread | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990552"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Предоставляет механизм для запуска кода в отладчике потока вызывающего объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pptc`  
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
 Модулям языка и узлам обычно используется этот метод для реализации свободнопоточный объекты на основе реализаций одного потоками.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)