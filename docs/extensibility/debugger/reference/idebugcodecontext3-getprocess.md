---
title: IDebugCodeContext3::GetProcess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81ee68246aa999c8ac610b9590f914388e6fbbf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876943"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Извлекает ссылку на интерфейс процесс отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcess(
    IDebugProcess2 **ppProcess
);
```

```csharp
public int GetProcess(
    out IDebugProcess2 ppProcess
);
```

#### <a name="parameters"></a>Параметры
`ppProcess`

 [out] Ссылка на интерфейс процесс отладки.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugCodeContext** объекта, который предоставляет [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) интерфейс.

```cpp
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)
{
    HRESULT hr = S_OK;
    CComPtr<CDebugEngine> pEngine;
    CComPtr<IDebugPort2> pPort2;

    IfFalseGo( ppProcess, E_INVALIDARG );
    *ppProcess = NULL;

    IfFalseGo( m_pProgram, E_FAIL );
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );

Error:

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
