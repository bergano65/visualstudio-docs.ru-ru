---
title: IDebugClassField::EnumNestedClasses | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b85d7a681d84f5549e0cb8f88d3c7a40773cc2f
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413206"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Создает перечислитель для классов, вложенные в этот класс.

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

#### <a name="parameters"></a>Параметры
`ppEnum`  
[out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных классов. Возвращает значение null, если нет вложенных классов.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если нет вложенных классов. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Каждый элемент перечисления является [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) описывающий вложенного класса.

Вложенный класс — это класс, определенный внутри другого класса. Пример:

```
class RootClass {
   class NestedClass { }
};
```

[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечисления будет содержать один объект, представляющий `NestedClass` класса.

## <a name="see-also"></a>См. также
[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)  
[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
