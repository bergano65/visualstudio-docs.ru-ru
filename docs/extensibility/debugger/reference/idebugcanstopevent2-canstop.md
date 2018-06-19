---
title: IDebugCanStopEvent2::CanStop | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3e2507ba86e00434c12a67ba70cad51fa5850ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108301"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Уведомляет отладчик (DE) ли Остановка текущей позиции кода или просто продолжить выполнение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fCanStop`  
 [in] Не равно нулю (`TRUE`) Если DE остановки в коде текущего расположения; в противном случае — нуль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Получатель данного события обычно вызывает [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) метод, чтобы определить причину DE хочет остановить, а затем вызывает `IDebugCanStopEvent2::CanStop` метод с соответствующий ответ.  
  
 При остановке DE, он отправляет событие, которое описывает причину остановки. Обычно существует два события, которые отправляются разрыв пользователя или сигнала, представленного [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) интерфейса и точка останова события, представленного [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)