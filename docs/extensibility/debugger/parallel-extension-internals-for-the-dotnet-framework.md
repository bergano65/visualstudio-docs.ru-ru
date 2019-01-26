---
title: Параллельная внутренние компоненты расширений для .NET Framework | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad538269f7c6cd11c6a3b93d60c283c5f63558ef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028655"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутренние компоненты параллельных расширений для .NET Framework
В этом разделе описываются внутренние типы, методы и поля классов, которые помогут вам реализовать пользовательского отладчика по параллельным расширениям для .NET Framework.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)  
 Описывает внутренние данные элементы <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса.  
  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Описывает внутренние данные элементы <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса.  
  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Описывает внутренние данные элементы `System.Threading.Tasks.ContingentProperties` класса.  
  
 [Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> структуры.  
  
 [AsyncTaskMethodBuilder\<TResult > структуры](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> структуры.  
  
 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Описывает внутренним членам объектов <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> структуры.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Параллельное программирование](/dotnet/standard/parallel-programming/index)