---
title: "IDebugApplication::SynchronousCallInDebuggerThread | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7b66b0b085c0fe3abbee3c3b8c5c3f7d252d3b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Предоставляет механизм для вызывающего объекта, для выполнения кода в поток отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 Модули языка и узлы обычно используется этот метод для реализации свободнопоточный объекты на основе реализаций одного однопотоковое.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)