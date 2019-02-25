---
title: IDebugCodeContext3::GetModule | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3::GetModule
ms.assetid: 8e4317b8-8255-486c-a896-a68ed94f8aa1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae925ab4c05db45d09638070df9291541f19a869
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703725"
---
# <a name="idebugcodecontext3getmodule"></a>IDebugCodeContext3::GetModule
Извлекает ссылку на интерфейс модуля отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetModule(
    IDebugModule2 **ppModule
);
```

```csharp
public int GetModule(
    out IDebugModule2 ppModule
);
```

#### <a name="parameters"></a>Параметры
`ppModule`

 [out] Ссылка на интерфейс модуля отладки.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugCodeContext** объекта, который предоставляет [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) интерфейс.

```cpp
HRESULT CDebugCodeContext::GetModule(IDebugModule2** ppModule)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;

    IfFalseGo( ppModule, E_INVALIDARG );
    *ppModule = NULL;

    IfFailGo( this->GetModule(&pModule) );
    IfFailGo( pModule->QueryInterface(IID_IDebugModule2, (void**) ppModule) );

Error:

    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
