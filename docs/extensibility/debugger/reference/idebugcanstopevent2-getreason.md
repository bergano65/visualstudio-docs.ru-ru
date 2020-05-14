---
title: IDebugCanStopEvent2::GetReason Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734520"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Получает причину, почему отладка двигателя (DE) хочет остановить.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Параметры
`pcr`\
(ваут) Возвращает значение из [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) перечисления, описывающие причину этого события.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод обычно вызывается перед методом [CanStop,](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) чтобы абонент мог`TRUE`определить, `IDebugCanStopEvent2::CanStop` следует ли передавать ненулевой ( ) к методу.

 Причиной остановки может `CANSTOP_ENTRYPOINT`быть либо, что означает, что `CANSTOP_STEPIN`DE достиг точки входа, или , что означает, что DE вошел в функцию.

## <a name="see-also"></a>См. также
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
