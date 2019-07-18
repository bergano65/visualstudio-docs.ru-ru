---
title: IDebugSymbolProvider::GetMethodFieldsByName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02b6947b36439610e41ec0a9e33ebc3f599a6c92
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347595"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Этот метод возвращает поле, представляющее полному имени метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`pszFullName`\
[in] Имя метода.

`nameMatch`\
[in] Выбирает тип соответствия, например, с учетом регистра.

`ppEnum`\
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечислитель для полей, связанных с помощью этого метода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Метод можно связать с несколькими полями, если он перегружен, например.

## <a name="see-also"></a>См. также
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)