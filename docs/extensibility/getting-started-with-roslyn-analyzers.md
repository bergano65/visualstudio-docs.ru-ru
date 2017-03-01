---
title: "Приступая к работе с Roslyn анализаторы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 6
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a71add3ac837e3727d54b379b6e82ee126e4a3f
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn
С помощью анализаторов динамическую, основанную на проект кода в Visual Studio авторы API может отправить анализ кода для конкретного домена как часть своих пакетов NuGet.  Поскольку эти анализаторов на базе платформы компилятора .NET (кодовое название «Roslyn»), они создают предупреждения в коде при вводе даже до завершения строки (больше нет ожидающих создания кода для обнаружения проблем).  Анализаторы, также могут возникать исправления автоматического кода из строки лампочки Visual Studio позволяет очистить коде немедленно  
  
## <a name="getting-started"></a>Начало работы  
 [Roslyn динамических анализаторов кода Общие сведения и пошаговое руководство](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Добавление кода устраняет Пошаговое руководство: Предоставления пользователям исправления проблем, анализатор](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Общие сведения и пошаговое руководство разговоров анализатора в реальном мире](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Реальном мире анализатор Roslyn](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , вы также можете посмотреть как [общаться](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Несколько примеров на github, сгруппированы в три вида анализаторы](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Введение и обзор анализаторов несколько](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## <a name="other-resources"></a>Другие ресурсы  
 [Дополнительные документы на сайте github ОС](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Правила FxCop реализуется с помощью анализаторов Roslyn на github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
