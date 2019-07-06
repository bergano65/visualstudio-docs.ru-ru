---
title: Начало работы с анализаторами Roslyn | Документация Майкрософт
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6a6f4123f72afd8c310e627a9da6759f4c4548a
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586959"
---
# <a name="get-started-with-roslyn-analyzers"></a>Начало работы с анализаторами Roslyn

С анализаторами динамическую, основанную на проект кода в Visual Studio авторы API могут поставляться анализа кода для конкретного домена как часть своих пакетов NuGet. Так как эти анализаторы работают на платформе компилятора .NET (кодовое название «Roslyn»), они создают предупреждения в коде при вводе еще до завершения строки (не более ожидания для сборки кода для обнаружения проблем). Анализаторы могут также возникать средство автоматического код из строки лампочки Visual Studio позволяет очистить коде немедленно.

## <a name="get-started"></a>Начало работы

[Обзор анализаторов Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Учебник. Написать первый анализатора и код исправления](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Добавление исправления кода Пошаговое руководство: Предоставления пользователям исправления проблем, анализатор](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Анализатор Roslyn в реальном мире](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , вы также можете посмотреть как [говорить](https://channel9.msdn.com/events/Build/2015/3-725)

[Несколько примеров на GitHub, сгруппированы в три вида анализаторы](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>См. также

- [Справочник по версии пакета платформы компилятора .NET](roslyn-version-support.md)
- [Дополнительные документы на сайте GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Правила FxCop, реализовано с помощью анализаторов Roslyn](http://roslynanalyzersstatus.azurewebsites.net/)
