---
title: СТЕПУНИТ Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a87c86647407d90c9f4292b1307fd5623e85d13b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713523"
---
# <a name="stepunit"></a>STEPUNIT
Определяет единицу шага для шага.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
typedef DWORD STEPUNIT;
```

```csharp
enum enum_STEPUNIT { 
   STEP_STATEMENT   = 0,
   STEP_LINE        = 1,
   STEP_INSTRUCTION = 2
};
```

## <a name="fields"></a>Поля
 `STEP_STATEMENT`\
 Шаги за заявлением.

 `STEP_LINE`\
 Шаги за строкой.

 `STEP_INSTRUCTION`\
 Шаги за инструкцией.

## <a name="remarks"></a>Примечания
 Прошел в качестве аргумента методу [Step.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)
