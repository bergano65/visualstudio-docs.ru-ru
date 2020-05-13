---
title: IDebugMethodField::EnumАргументы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727261"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Создает регистратор для типа каждого аргумента, необходимого для вызова метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Параметры
`ppParams`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список типов аргументов. Возвращает нулевую стоимость, если нет аргументов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE, если нет аргументов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент представляет собой объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий типы каждого параметра. Позвоните в метод [GetInfo,](../../../extensibility/debugger/reference/idebugfield-getinfo.md) чтобы получить информацию о типе каждого параметра.

 Если имя параметра необходимо вместе с типом, то позвоните методу [EnumParameters.](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
