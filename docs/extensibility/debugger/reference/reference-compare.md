---
title: REFERENCE_COMPARE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd36ad090a0b354744becf7140ff0d0785588eb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922878"
---
# <a name="reference_compare"></a>REFERENCE_COMPARE
Указывает тип сравнения для ссылок.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>Поля
 `REF_COMPARE_EQUAL`\
 Задает сравнение равенства.

 `REF_COMPARE_LESS_THAN`\
 Указывает сравнение "меньше чем".

 `REF_COMPARE_GREATER_THAN`\
 Задает сравнение "больше чем".

## <a name="remarks"></a>Remarks
 Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugreference2-compare.md)
