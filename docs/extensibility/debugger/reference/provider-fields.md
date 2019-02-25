---
title: PROVIDER_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67c055c1cf9fffde227d4e52a9764b2559a2342b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684355"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
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

## <a name="members"></a>Участники
 PFIELD_PROGRAM_NODES `ProgramNodes` поле является допустимым.

 PFIELD_IS_DEBUGGER_PRESENT `fIsDebuggerPresent` поле является допустимым.

## <a name="remarks"></a>Примечания
 Эти значения возвращаются в `Fields` членом [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) структуры, чтобы указать, какие поля структуры явно были заполнены.

 Эти значения могут объединяться с побитовым объектом `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)