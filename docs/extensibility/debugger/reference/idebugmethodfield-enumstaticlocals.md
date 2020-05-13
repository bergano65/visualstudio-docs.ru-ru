---
title: IDebugMethodfield::EnumStaticLocals Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e0a89b4c1ac4318b6dd070dc086b86b45ad24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727153"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Создает регистратор для статических локальных переменных метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumStaticLocals( 
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumStaticLocals(
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Параметры
`ppLocals`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список статических местных жителей. Возвращает нулевую стоимость, если нет статических местных жителей.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK или возвращается S_FALSE, если Нет статических местных жителей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент представляет собой объект [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий различные типы статических местных жителей. Вызов метод [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) на каждом объекте, чтобы точно определить, какой статическое локальное объект представляет.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
