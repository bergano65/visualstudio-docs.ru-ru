---
title: IDebugObject2:GetBackingfieldForProperty Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726243"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Получает поле или переменную (если таковая имеется), которая может поддерживать свойство, представленное этим объектом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Параметры
`ppObject`\
(ваут) Объект [IDebugObject2,](../../../extensibility/debugger/reference/idebugobject2.md) описывающий резервное поле.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Объект [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) представляет собой свойство управляемого класса кода, т.е. метод с доступом get and/or set. Такие свойства обычно требуют переменной, чтобы содержать значение, которым манипулирует свойство. Эта переменная известна как резервное поле. Если нет резервного поля для объекта, то убедитесь, что вернуть нулевую стоимость: некоторые абоненты могут не обращать `ppObject`внимания на значение возврата, но вместо этого будут смотреть, чтобы увидеть, если нулевая стоимость была возвращена дюйма

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
