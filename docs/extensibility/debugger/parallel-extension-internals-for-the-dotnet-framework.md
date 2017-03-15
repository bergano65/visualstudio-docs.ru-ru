---
title: "Параллельные внутри расширения для платформы .NET Framework | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c679d573bde8352906471b4eded7ccb9051f5959
ms.lasthandoff: 02/22/2017

---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутренние компоненты параллельных расширений для .NET Framework
В этом разделе описывает внутренние типы, методы и поля из классов, которые помогают реализовать пользовательские отладчика по параллельным расширениям для .NET Framework.  
  
## <a name="in-this-section"></a>Содержание  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)  
 Описывает внутренние данные-члены <xref:System.Threading.Tasks.Task?displayProperty=fullName>класса.</xref:System.Threading.Tasks.Task?displayProperty=fullName>  
  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Описывает внутренние данные-члены <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>класса.</xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>  
  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Описывает внутренние данные-члены из `System.Threading.Tasks.ContingentProperties` класса.  
  
 [Структура AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы из <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>структуры.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>  
  
 [AsyncTaskMethodBuilder\<TResult настроек структуры](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Описывает внутренние элементы из <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>структуры.</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>  
  
 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы из <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>структуры.</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>  
  
## <a name="see-also"></a>См. также  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName></xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Расширение возможностей отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Параллельное программирование](http://msdn.microsoft.com/Library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
