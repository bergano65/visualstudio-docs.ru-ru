---
title: IDebugClassField::EnumNestedEnums | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdfa97ccdbf139ce28ec58c07864551c4e6a7d5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922648"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Создает перечислитель для вложенных перечислителей этого класса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Параметры
`ppEnum`

 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных перечислений. Возвращает значение null, если нет вложенных перечислений.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если нет вложенной перечислителей. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
Каждый элемент перечисления является [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) описывающий вложенных перечисления.

Перечисление при объявлении внутри класса считается вложенных перечисления. Например, если учитывать, что:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums` Метод вернет [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) , содержащий один [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) , представляющий `NestedEnum` перечисления.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
