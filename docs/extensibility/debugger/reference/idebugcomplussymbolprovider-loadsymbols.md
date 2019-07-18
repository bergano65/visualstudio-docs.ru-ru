---
title: IDebugComPlusSymbolProvider::LoadSymbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- LoadSymbols
- IDebugComPlusSymbolProvider::LoadSymbols
ms.assetid: 3499680d-0b9a-4f20-8432-c89a41b29b87
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5194b13a1e92b6d6f8ed4b688ea7956cb3ed876e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309005"
---
# <a name="idebugcomplussymbolproviderloadsymbols"></a>IDebugComPlusSymbolProvider::LoadSymbols
Загружает указанный отладочные символы в памяти.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    BSTR      bstrModuleName,
    BSTR      bstrSymSearchPath
);
```

```csharp
int LoadSymbols(
    uint   ulAppDomainID,
    Guid   guidModule,
    ulong  baseAddress,
    object pUnkMetadataImport,
    string bstrModuleName,
    string bstrSymSearchPath
);
```

## <a name="parameters"></a>Параметры
`ulAppDomainID`\
[in] Идентификатор домена приложения.

`guidModule`\
[in] Уникальный идентификатор mondule.

`baseAddress`\
[in] Базовый адрес памяти.

`pUnkMetadataImport`\
[in] Объект, содержащий метаданные символ.

`bstrModuleName`\
[in] Имя модуля.

`bstrSymSearchPath`\
[in] Путь для поиска файла символов.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для **CDebugSymbolProvider** объекта, который предоставляет [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) интерфейс.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* _pMetadata,
    BSTR bstrModule,
    BSTR bstrSearchPath)
{
    return LoadSymbolsWithCorModule(ulAppDomainID, guidModule, baseOffset, _pMetadata, NULL, bstrModule, bstrSearchPath);
}
```

## <a name="see-also"></a>См. также
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
