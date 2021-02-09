---
title: 'Идебугклассфиелд:: Енумнестедклассес | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63b42df8181ca12da1be2aca6faf1346406b621f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877438"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Создает перечислитель для классов, вложенных в этот класс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNestedClasses(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedClasses(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) , представляющий список вложенных классов. Возвращает значение null, если нет вложенных классов.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает S_OK или возвращает S_FALSE, если нет вложенных классов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
Каждый элемент перечисления — это объект [идебугклассфиелд](../../../extensibility/debugger/reference/idebugclassfield.md) , описывающий вложенный класс.

Вложенный класс — это класс, определенный внутри другого класса. Пример:

```
class RootClass {
   class NestedClass { }
};
```

Перечисление [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md) будет содержать один объект, представляющий `NestedClass` класс.

## <a name="see-also"></a>См. также раздел
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
