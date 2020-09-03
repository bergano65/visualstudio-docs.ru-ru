---
title: PROVIDER_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f64b455ab0331f9b8f08da1f29a3e2c1b82fdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713789"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
Указывает свойства, связанные с поставщиком программы.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Поля
 `PFIELD_PROGRAM_NODES`\
 `ProgramNodes`Поле является допустимым.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 `fIsDebuggerPresent`Поле является допустимым.

## <a name="remarks"></a>Remarks
 Эти значения возвращаются в элементе `Fields` структуры [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) , чтобы указать, какие поля структуры были явно заполнены.

 Эти значения можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
