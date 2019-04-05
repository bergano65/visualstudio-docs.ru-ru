---
title: IDebugCanStopEvent2::CanStop | Документация Майкрософт
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992456"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Уведомляет отладчик (DE), ли отменить в текущем положении кода или просто продолжить выполнение.  
  
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
 [in] Ненулевое значение (`TRUE`) Если DE остановки в текущее расположение кода; в противном случае — нуль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Получатель этого события обычно не вызывает [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) метод, чтобы определить причину DE хочет остановить, а затем вызывает `IDebugCanStopEvent2::CanStop` метод с соответствующий ответ.  
  
 Если перестает DE, он отправляет событие, описывающее причину остановки. Обычно существуют два события, которые отправляются разрыв пользователя или сигнала, представленный [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) интерфейса и событие точки останова, представленный [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
