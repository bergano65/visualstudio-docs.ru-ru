---
title: Параллельная внутренние компоненты расширений для .NET Framework | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351482"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутренние компоненты параллельных расширений для .NET Framework
В этом разделе описываются внутренние типы, методы и поля классов, которые помогут вам реализовать пользовательского отладчика по параллельным расширениям для .NET Framework.

## <a name="in-this-section"></a>Содержание раздела
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md) Описывает внутренние данные элементы <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса.

 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Описывает внутренние данные элементы <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса.

 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Описывает внутренние данные элементы `System.Threading.Tasks.ContingentProperties` класса.

 [Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> структуры.

 [AsyncTaskMethodBuilder\<TResult > Структура](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> структуры.

 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> структуры.

## <a name="see-also"></a>См. также
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Параллельное программирование](/dotnet/standard/parallel-programming/index)