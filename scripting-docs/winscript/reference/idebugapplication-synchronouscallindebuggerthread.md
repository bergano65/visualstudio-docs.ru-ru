---
title: 'IDebugApplication:: Синчронаускаллиндебугжерсреад | Документация Майкрософт'
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
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574588"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Предоставляет механизм для выполнения кода в потоке отладчика.  
  
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
 окне Объект для вызова.  
  
 `dwParam1`  
 окне Первый параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 окне Второй параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 окне Третий параметр для передачи в метод `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Языковые механизмы и узлы обычно используют этот метод для реализации свободных потоков объектов поверх отдельных потоков реализации.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)