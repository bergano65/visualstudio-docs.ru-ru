---
title: STEPKIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7adf835cd3809eeb3d4db664cf5febcfa2a0597b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329161"
---
# <a name="stepkind"></a>STEPKIND
Задает тип шага для пошагового выполнения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Поля
 `STEP_INTO`\
 Шаг с заходом в функцию.

 `STEP_OVER`\
 Шаги с обходом функции.

 `STEP_OUT`\
 Выходит из функции.

 `STEP_BACKWARDS`\
 Переход обратно в функцию.

## <a name="remarks"></a>Примечания
 Передается в качестве аргумента для [шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)