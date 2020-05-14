---
title: OBJECT_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714131"
---
# <a name="object_type"></a>Object_Type
Определяет тип объекта из оценщика выражения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Поля
 `OBJECT_TYPE_BOOLEAN`\
 Означает, что объект является булеаном.

 `OBJECT_TYPE_CHAR`\
 Означает, что объект является символом.

 `OBJECT_TYPE_I1`\
 Означает, что объект представляет собой один байт, подписанный в один ряд.

 `OBJECT_TYPE_U1`\
 Означает, что объект представляет собой один байт неподписанный ряд.

 `OBJECT_TYPE_I2`\
 Означает, что объект представляет собой двухбайт подписанный ряд.

 `OBJECT_TYPE_U2`\
 Означает, что объект представляет собой двухбайный неподписанный ряд.

 `OBJECT_TYPE_I4`\
 Означает, что объект представляет собой четырехбайт подписанный ряд.

 `OBJECT_TYPE_U4`\
 Означает, что объект представляет собой четырехбайт ный неподписанный ряд.

 `OBJECT_TYPE_I8`\
 Означает, что объект представляет собой восьмибайтподписанный ряд.

 `OBJECT_TYPE_U8`\
 Означает, что объект представляет собой восьмибайтный неподписанный ряд.

 `OBJECT_TYPE_R4`\
 Означает, что объект представляет собой четырехбайное плавающее точечное число.

 `OBJECT_TYPE_R8`\
 Означает, что объект представляет собой восьмибайтное плавающее точечное число.

 `OBJECT_TYPE_OBJECT`\
 Означает, что объект является объектом.

 `OBJECT_TYPE_NULL`\
 Означает, что объект является NULL.

 `OBJECT_TYPE_CLASS`\
 Означает, что объект является классом.

## <a name="remarks"></a>Примечания
 Прошел в качестве аргумента методам [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) и [CreateArrayObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
