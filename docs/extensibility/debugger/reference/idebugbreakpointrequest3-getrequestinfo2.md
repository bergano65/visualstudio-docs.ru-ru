---
title: IDebugBreakpointЗапрос3::GetRequestInfo2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5febf664da9cd69dbd88b70056d9eac953bf581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734835"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Этот метод получает информацию о запросе точки разрыва, описывающая этот запрос точки разрыва.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRequestInfo2(
   BPREQI_FIELDS      dwFields,
   BP_REQUEST_INFO2*  bBPRequestInfo
);
```

```csharp
int GetRequestInfo2(
   enum_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO2[]  bBPRequestInfo
);
```

## <a name="parameters"></a>Параметры
`dwFields`\
(в) Сочетание флагов [из BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисления, определяющих, какие поля должны быть `pBPRequestInfo` заполнены.

`bBPRequestInfo`\
(ваут) [Структура BP_REQUEST_INFO2,](../../../extensibility/debugger/reference/bp-request-info2.md) которая должна быть заполнена.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В этом запросе больше информации, чем возвращается из метода [GetRequestInfo.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)

## <a name="see-also"></a>См. также
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
