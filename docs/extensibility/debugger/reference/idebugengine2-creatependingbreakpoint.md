---
title: IDebugEngine2::CreatePendingBreakpoint | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fdd7fde0540754df3b152eb38d729576a7b9fe26
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333307"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Создает точку останова в модуль отладки (DE).

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
[in] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , описывающий ожидающая точка останова для создания.

`ppPendingBP`\
[out] Возвращает [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий ожидающая точка останова.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Обычно возвращает `E_FAIL` Если `pBPRequest` параметр не соответствует любой язык, поддерживаемый DE, если `pBPRequest` параметр недопустима или неполна.

## <a name="remarks"></a>Примечания
Ожидание точка останова — это преимущественно коллекция все сведения, необходимые для привязки точку останова для кода. Ожидающая точка останова, возвращаемый этим методом не привязан к кода до [привязать](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) вызывается метод.

Для каждого ожидающего точки останова наборы пользователей, диспетчер отладки сеансов (SDM) вызывает этот метод в каждой присоединенного DE. Возлагается DE, чтобы убедиться, что точка останова является допустимым для программ, работающих в этом DE.

Когда пользователь устанавливает точку останова на строке кода, DE может выполнять привязку точки останова в ближайшую строку в документе, который соответствует этот код. Это позволяет пользователю установить точку останова в первой строке многострочного оператора, но привязать его в последней строке (где весь код помечается с помощью отладочной информации).

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объекта. Реализация DE `IDebugEngine2::CreatePendingBreakpoint` может пересылать все вызовы этой реализации метода в каждой программе.

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
