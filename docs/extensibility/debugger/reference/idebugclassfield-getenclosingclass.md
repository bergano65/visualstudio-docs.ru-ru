---
title: IDebugClassfield::GetEnclosingClass Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734391"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Получает класс, который примыкает к этому классу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Параметры
`ppClassField`\
(ваут) Возвращает объект [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) представляющий класс прилагающего. Возвращает нулевую стоимость, если нет прилагательного класса.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Если класс, представленный этим объектом [IDebugClassField,](../../../extensibility/debugger/reference/idebugclassfield.md) является `ppClassField` вложенным `IDebugClassField` классом, то параметр возвращает объект, представляющий класс прилагающего. Например, с таким определением класса:

```
class RootClass {
    class NestedClass { }
};
```

Вызов `GetEnclosingClass` метода `IDebugClassField` на объект, `NestedClass` представляющий `IDebugClassField` класс, возвращает `RootClass`объект, представляющий класс.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
