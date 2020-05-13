---
title: IDebugClassField::EnumConstructors Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734466"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Создает регистратор для конструкторов для этого класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`cMatch`\
(в) Значение из [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) перечисления, которое определяет тип конструкторов для перечисления.

`ppEnum`\
(ваут) Возвращает объект [IEnumDebugFields,](../../../extensibility/debugger/reference/ienumdebugfields.md) представляющий список конструкторов. Возвращает нулевую стоимость, если нет конструкторов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK или возвращает S_FALSE, если Нет конструкторов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Каждый элемент перечисления представляет собой объект [IDebugMethodField,](../../../extensibility/debugger/reference/idebugmethodfield.md) описывающий метод конструктора.

 Список конструкторов обычно не включает конструкторы по умолчанию, поставляемые компилятором.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
