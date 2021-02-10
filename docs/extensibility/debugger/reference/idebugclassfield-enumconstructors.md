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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05226572d7f1b708745887338c654674e71d0f5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947086"
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
