---
title: 'IDebugEngine2:: Креатепендингбреакпоинт | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93534a40d523c7b67a769ebea319463cf59e4b7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879024"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Создает отложенную точку останова в модуле отладки (DE).

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
окне Объект [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , описывающий отложенную точку останова для создания.

`ppPendingBP`\
заполняет Возвращает объект [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , представляющий ожидающие точки останова.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Обычно возвращает значение `E_FAIL` , если `pBPRequest` параметр не соответствует ни одному из языков, поддерживаемых de, если `pBPRequest` параметр является недопустимым или неполным.

## <a name="remarks"></a>Remarks
Ожидающая точка останова по сути является коллекцией всех сведений, необходимых для привязки точки останова к коду. Ожидающая точка останова, возвращенная этим методом, не привязана к коду до вызова метода [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .

Для каждой ожидающей точки останова, заданной пользователем, диспетчер отладки сеансов (SDM) вызывает этот метод в каждом присоединенном DE. Чтобы убедиться в том, что точка останова является допустимой для программ, запущенных в этой сети.

Когда пользователь устанавливает точку останова в строке кода, DE может привязать точку останова к ближайшей строке документа, соответствующей этому коду. Это дает пользователю возможность установить точку останова на первой строке многострочного оператора, но привязать ее к последней строке (где весь код имеет атрибут в отладочной информации).

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CProgram` объекта. После этого реализация DE `IDebugEngine2::CreatePendingBreakpoint` может пересылать все вызовы данной реализации метода в каждой программе.

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

## <a name="see-also"></a>См. также раздел
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Выполняется](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
