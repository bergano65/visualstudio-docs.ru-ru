---
title: MACHINE_INFO_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714495"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Определяет, какую информацию получить для конкретной машины.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Поля
 `MCIF_NAME`\
 Инициализация/использование `bstrName` поля в структуре.

 `MCIF_FLAGS`\
 Инициализация/использование `Flags` поля в структуре.

 `MIF_ALL`\
 Инициализация/использование всех полей в структуре.

## <a name="remarks"></a>Примечания
 Эти значения передаются методу [GetMachineInfo,](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) чтобы указать, какие члены [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) структуры должны быть инициализированы.

 Также используется `Fields` в составе `MACHINE_INFO` структуры для обозначения того, какие поля используются и действительны.

 Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
