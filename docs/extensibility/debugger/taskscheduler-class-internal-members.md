---
title: Класс TaskScheduler — внутренние элементы | Документация Майкрософт
description: Сведения о внутренних членах класса System. Threading. Tasks. TaskScheduler, которые помогают реализовать пользовательский отладчик.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0ed72efb383e216d5998c2231a472b8d29f9ec4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837454"
---
# <a name="taskscheduler-class---internal-members"></a>Класс TaskScheduler — внутренние элементы
В этой статье описываются внутренние члены <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса, помогающие реализовать пользовательский отладчик. Общие сведения об этом классе см <xref:System.Threading.Tasks.TaskScheduler> . в справочной статье.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этим внутренним членам из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Члены

### <a name="methods"></a>Методы

|Имя|Описание|
|----------|-----------------|
|[жетсчедуледтасксфордебугжер](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Извлекает массив всех запланированных задач.|
|[жеттасксчедулерсфордебугжер](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Извлекает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент.|

## <a name="remarks"></a>Remarks

## <a name="see-also"></a>См. также раздел
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Внутренние модули параллельного расширения для платформа .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
