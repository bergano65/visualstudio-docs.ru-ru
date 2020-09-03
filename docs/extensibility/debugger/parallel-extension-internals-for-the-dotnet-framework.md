---
title: Внутренние модули параллельного расширения для .NET Framework | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738271"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутренние модули параллельного расширения для .NET Framework
В этом разделе описываются внутренние типы, методы и поля классов, которые помогают реализовать пользовательский отладчик для параллельных расширений .NET Framework.

## <a name="in-this-section"></a>В этом разделе
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md) Описывает внутренние элементы данных <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса.

 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Описывает внутренние элементы данных <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса.

 [Класс континжентпропертиес](../../extensibility/debugger/contingentproperties-class-internal-members.md) Описывает внутренние элементы данных `System.Threading.Tasks.ContingentProperties` класса.

 [Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> структуры.

 [ \<TResult> Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> структуры.

 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> структуры.

## <a name="see-also"></a>См. также раздел
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Параллельное программирование](/dotnet/standard/parallel-programming/index)
