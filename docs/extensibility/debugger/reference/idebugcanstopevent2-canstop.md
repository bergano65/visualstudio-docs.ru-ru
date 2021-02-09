---
title: 'IDebugCanStopEvent2:: Канстоп | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d3563fb46b9117ff7f142c5822c708deda34fda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881000"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Уведомляет модуль отладки (DE), следует ли останавливаться на текущем расположении кода или просто продолжить выполнение.

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

## <a name="parameters"></a>Параметры
`fCanStop`\
окне Ненулевое значение ( `TRUE` ), если de должен останавливаться в текущем расположении кода; в противном случае — ноль ( `FALSE` ).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Получатель этого события обычно [вызывает метод GetResponse, чтобы](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) определить причину, по которой de пытается останавливаться, а затем вызывает `IDebugCanStopEvent2::CanStop` метод с соответствующим ответом.

 Если параметр DE остановлен, отправляется событие, описывающее причину остановки. Обычно передаются два события: пользователь или сигнал, представленный интерфейсом [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) , и событие точки останова, представленное интерфейсом [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
