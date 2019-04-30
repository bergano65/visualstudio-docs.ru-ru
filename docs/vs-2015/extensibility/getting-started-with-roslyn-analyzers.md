---
title: Начало работы с анализаторами Roslyn | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 104e3a30589f5892c1440266afd7917486d704ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546654"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С анализаторами динамическую, основанную на проект кода в Visual Studio авторы API могут поставляться анализа кода для конкретного домена как часть своих пакетов NuGet.  Так как эти анализаторы работают на платформе компилятора .NET (кодовое название «Roslyn»), они создают предупреждения в коде при вводе еще до завершения строки (не более ожидания для сборки кода для обнаружения проблем).  Анализаторы могут также возникать средство автоматического код из строки лампочки Visual Studio позволяет очистить коде немедленно

## <a name="getting-started"></a>Начало работы
[Анализаторы Roslyn кода в реальном времени введение и пошаговое руководство](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Добавление кода для решения Пошаговое руководство: Предоставления пользователям исправления проблем, анализатор](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Общие сведения и пошаговое руководство разговоров анализатора в реальном мире](http://channel9.msdn.com/events/Build/2015/3-725)

[Анализатор Roslyn real World](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , вы также можете посмотреть как [говорить](http://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на GitHub, сгруппированы в три вида анализаторы](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Введение и обзор несколько анализаторов](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Другие ресурсы
[Дополнительные документы на сайте GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Правила FxCop, реализовано с помощью анализаторов Roslyn на GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
