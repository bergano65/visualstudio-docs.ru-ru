---
title: ADDRESS_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71888e4e0b339b9b9b94946e8d9c49f8ffb1f84c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696824"
---
# <a name="addresskind"></a>ADDRESS_KIND
Указывает типы адресов.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="terms"></a>Термины
ADDRESS_KIND_NATIVE значения собственный адрес, представленный [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) структуры.

ADDRESS_KIND_UNMANAGED_THIS_RELATIVE неуправляемый адрес относительно `this` (`Me` в Visual Basic) указатель и представленный [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) структуры.

ADDRESS_KIND_UNMANAGED_PHYSICAL неуправляемый физический адрес, представленный [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) структуры.

Метод ADDRESS_KIND_METHOD объект класса, представленного [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) структуры.

Поле ADDRESS_KIND_FIELD типа класса, представленного [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) структуры.

ADDRESS_KIND_LOCAL адрес для локальной переменной и представленный [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) структуры.

ADDRESS_KIND_PARAM объект параметр метода или функции, представленной [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) структуры.

ADDRESS_KIND_ARRAYELEM элемент массива, представленный [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) структуры.

ADDRESS_KIND_RETVAL типа возвращаемого значения, представленного [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) структуры.

## <a name="remarks"></a>Примечания
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) возвращает [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры, который содержит объединение множества возможных структур [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры. `dwKind` Поле `DEBUG_ADDRESS_UNION` структуры содержит `ADDRESS_KIND` значение и описывается, как интерпретировать поле объединения.

## <a name="requirements"></a>Требования
Заголовок: sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
