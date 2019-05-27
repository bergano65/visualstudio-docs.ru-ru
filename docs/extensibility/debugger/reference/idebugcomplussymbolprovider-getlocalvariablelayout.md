---
title: IDebugComPlusSymbolProvider::GetLocalVariablelayout | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 840f7ec69c902debc2ce704fcbdd65e4b034038a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206388"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
Извлекает структуру локальных переменных для набора методов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLocalVariablelayout(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONG32   cMethods,
    _mdToken  rgMethodTokens[],
    IStream** pStreamLayout
);
```

```csharp
int GetLocalVariablelayout(
    uint        ulAppDomainID,
    Guid        guidModule,
    uint        cMethods,
    int[]       rgMethodTokens,
    out IStream pStreamLayout
);
```

## <a name="parameters"></a>Параметры
`ulAppDomainID`\
[in] Идентификатор домена приложения.

`guidModule`\
[in] Уникальный идентификатор модуля.

`cMethods`\
[in] Число метод токены `rgMethodTokens` массива.

`rgMethodTokens`\
[in] Массив, метод маркеров.

`pStreamLayout`\
[out] Текстовый поток, содержащий структуру переменных.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) интерфейс.

```cpp
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONG32 cMethods,
    _mdToken rgMethodTokens[],
    IStream** ppStreamLayout)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);

    CComPtr<ISymUnmanagedReader> symReader;
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));
    CComPtr<IStream> stream;
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));

    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)
    {
        CComPtr<ISymUnmanagedMethod> method;
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));
        CComPtr<ISymUnmanagedScope> rootScope;
        IfFailRet(method->GetRootScope(&rootScope));

        //
        // Add the method's variables to the stream
        //
        IfFailRet(AddScopeToStream(rootScope, 0, stream));

        // do end of method marker
        ULONG32 depth = 0xFFFFFFFF;
        ULONG cb = 0;
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));
    }

    LARGE_INTEGER pos;
    pos.QuadPart = 0;
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));
    *ppStreamLayout = stream.Detach();

    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);
    return hr;
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
