---
title: Класс TaskScheduler - Внутренние участники Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712569"
---
# <a name="taskscheduler-class---internal-members"></a>Класс TaskScheduler - Внутренние члены
В этой статье описаны <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> внутренние члены класса, которые помогают реализовать пользовательский отладчик. Для получения общей информации <xref:System.Threading.Tasks.TaskScheduler> об этом классе см.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Поскольку вы не можете получить доступ к этим внутренним членам из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Участники

### <a name="methods"></a>Методы

|name|Описание|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Извлекает массив всех запланированных задач.|
|[GetTaskПланировщиксдляДебуггер](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Извлекает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые в настоящее время активны.|

## <a name="remarks"></a>Примечания

## <a name="see-also"></a>См. также
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Параллельные внутренние расширения для рамочной программы .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
