---
title: Параллельные внутри расширения для платформы .NET Framework | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4936efe50023ed1e193d0c2ec0d9c3423ac5cc64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутри параллельной расширения для платформы .NET Framework
Этот раздел описывает внутренние типы, методы и поля из классов, которые помогают реализовать пользовательские отладчик для параллельных расширений для .NET Framework.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Task-класс](../../extensibility/debugger/task-class-internal-members.md)  
 Описывает внутренние данные-члены <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса.  
  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Описывает внутренние данные-члены <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса.  
  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Описывает внутренние данные-члены `System.Threading.Tasks.ContingentProperties` класса.  
  
 [Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> структуры.  
  
 [AsyncTaskMethodBuilder\<TResult > структуры](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> структуры.  
  
 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> структуры.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Расширения отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Параллельное программирование](/dotnet/standard/parallel-programming/index)