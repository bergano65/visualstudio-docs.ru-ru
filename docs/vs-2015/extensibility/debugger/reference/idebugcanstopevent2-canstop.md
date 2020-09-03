---
title: 'IDebugCanStopEvent2:: Канстоп | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191189"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Уведомляет модуль отладки (DE), следует ли останавливаться на текущем расположении кода или просто продолжить выполнение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Ненулевое значение ( `TRUE` ), если de должен останавливаться в текущем расположении кода; в противном случае — ноль ( `FALSE` ).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Получатель этого события обычно [вызывает метод GetResponse, чтобы](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) определить причину, по которой de пытается останавливаться, а затем вызывает `IDebugCanStopEvent2::CanStop` метод с соответствующим ответом.  
  
 Если параметр DE остановлен, отправляется событие, описывающее причину остановки. Обычно передаются два события: пользователь или сигнал, представленный интерфейсом [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) , и событие точки останова, представленное интерфейсом [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
