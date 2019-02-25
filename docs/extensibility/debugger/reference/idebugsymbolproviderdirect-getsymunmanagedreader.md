---
title: IDebugSymbolProviderDirect::GetSymUnmanagedReader | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0c038a7aa2b398a2ee58101248d2968913ba3b4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695184"
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
Получает средство чтения символов для неуправляемого кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSymUnmanagedReader (
   ULONG32    ulAppDomainID,
   GUID       guidModule,
   IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader (
   uint       ulAppDomainID,
   Guid       guidModule,
   out object ppSymUnmanagedReader
);
```

#### <a name="parameters"></a>Параметры
 `ulAppDomainID`

 [in] Идентификатор домена приложения.

 `guidModule`

 [in] Уникальный идентификатор модуля.

 `ppSymUnmanagedReader`

 [out] Возвращает объект, представляющий средства чтения символов для неуправляемого кода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)