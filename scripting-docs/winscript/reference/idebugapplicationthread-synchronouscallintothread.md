---
title: 'Идебугаппликатионсреад:: Синчронаускаллинтосреад | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574496"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Предоставляет механизм для выполнения кода в потоке приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstcb`  
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
 Этот метод предоставляет механизм для выполнения кода в потоке отладчика. Языковые механизмы и узлы обычно используют этот метод для реализации свободных потоков объектов поверх отдельных потоков реализации.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугаппликатионсреад](../../winscript/reference/idebugapplicationthread-interface.md)  
 [Интерфейс IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)