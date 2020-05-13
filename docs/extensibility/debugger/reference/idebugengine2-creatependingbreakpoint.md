---
title: IDebugEngine2::СозданиеВ ожиданииТочка (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731119"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Создает ожидающий момент разрыва в движке отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Параметры
`pBPRequest`\
(в) Объект [IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) описывающий отложенную точку разрыва для создания.

`ppPendingBP`\
(ваут) Возвращает объект [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) представляющий ожидачий точку разрыва.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Обычно `E_FAIL` возвращается, `pBPRequest` если параметр не соответствует языку, поддерживаемому DE, если `pBPRequest` параметр является недействительным или неполным.

## <a name="remarks"></a>Примечания
Ожидаемая точка разрыва по существу представляет собой набор всей информации, необходимой для привязки точки разрыва к коду. Ожидаемая точка разрыва, возвращенная из этого метода, не привязана к коду до тех пор, пока не будет вызван метод [Bind.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

Для каждого ожидающего завершения момента, который устанавливает пользователь, диспетчер сеанса отладки (SDM) вызывает этот метод в каждом присоединенном DE. Это до DE, чтобы убедиться, что точка разрыва действительна для программ, работающих в этом DE.

Когда пользователь устанавливает точку разрыва на строке кода, DE может связать точку разрыва с ближайшей строкой в документе, которая соответствует этому коду. Это позволяет пользователю установить точку разрыва на первой строке многолиневого оператора, но связать ее на последней строке (где весь код приписывается информации об отладке).

## <a name="example"></a>Пример
В следующем примере показано, как `CProgram` реализовать этот метод для простого объекта. Реализация DE `IDebugEngine2::CreatePendingBreakpoint` может затем направить все вызовы для этой реализации метода в каждой программе.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
