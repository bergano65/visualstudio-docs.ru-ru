---
title: 'Идебугклассфиелд:: Енумконструкторс | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734466"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Создает перечислитель для конструкторов этого класса.

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
окне Значение из перечисления [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) , указывающее тип конструкторов для перечисления.

`ppEnum`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список конструкторов. Возвращает значение null, если нет конструкторов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK или возвращает S_FALSE, если нет конструкторов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Каждый элемент перечисления — это объект [идебугмесодфиелд](../../../extensibility/debugger/reference/idebugmethodfield.md) , описывающий метод-конструктор.

 Список конструкторов обычно не включает конструкторы по умолчанию, предоставляемые компилятором.

## <a name="see-also"></a>См. также раздел
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
