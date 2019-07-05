---
title: OBJECT_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 726e4978ac2c474b1f23b90f409f25b8a58aceab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349920"
---
# <a name="objecttype"></a>OBJECT_TYPE
Указывает тип объекта из средство оценки выражений.

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
 Указывает, что объект является логическое значение.

 `OBJECT_TYPE_CHAR`\
 Указывает, что объект является знаком.

 `OBJECT_TYPE_I1`\
 Указывает, что объект является однобайтовое целое число со знаком.

 `OBJECT_TYPE_U1`\
 Указывает, что объект является однобайтовое целое число без знака.

 `OBJECT_TYPE_I2`\
 Указывает, что объект находится двухбайтовое целое число со знаком.

 `OBJECT_TYPE_U2`\
 Указывает, что объект находится двухбайтовое целое число без знака.

 `OBJECT_TYPE_I4`\
 Указывает, что объект является четырехбайтовое целое число со знаком.

 `OBJECT_TYPE_U4`\
 Указывает, что объект является 4 байтовым беззнаковым целым числом.

 `OBJECT_TYPE_I8`\
 Указывает, что объект является 8 байтовое целое число со знаком.

 `OBJECT_TYPE_U8`\
 Указывает, что объект является 8 байтовое целое число без знака.

 `OBJECT_TYPE_R4`\
 Указывает, что объект является числом с плавающей запятой размером 4 байта.

 `OBJECT_TYPE_R8`\
 Указывает, что объект является 8 байтовое число с плавающей запятой.

 `OBJECT_TYPE_OBJECT`\
 Указывает, что объект является объектом.

 `OBJECT_TYPE_NULL`\
 Указывает, что объект имеет значение NULL.

 `OBJECT_TYPE_CLASS`\
 Указывает, что объект является классом.

## <a name="remarks"></a>Примечания
 Передается в качестве аргумента для [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) и [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) методы.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)