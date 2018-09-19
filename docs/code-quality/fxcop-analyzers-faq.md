---
title: Анализ кода FxCop и анализаторы FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136370"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Часто задаваемые вопросы о FxCop и FxCop анализаторы

Он может быть немного сбить с толку сведения о различиях между устаревших FxCop и FxCop анализаторы. Эта статья призвана решить некоторые вопросы, которые могут возникнуть.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Какова разница между устаревших FxCop и FxCop анализаторы?

Устаревшие FxCop выполняет анализ после построения скомпилированной сборки. Он выполняется как отдельный исполняемый файл с именем **FxCopCmd.exe**. FxCopCmd.exe загружают скомпилированную сборку, запускает анализ кода и затем результаты (или *диагностики*).

Анализаторы FxCop основаны на платформе компилятора .NET («Roslyn»). Вы [установить их в виде пакета NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) , на который ссылается проект или решение. Анализаторы FxCop, запуска исходного кода на основе анализа во время выполнения компилятора. Анализаторы FxCop размещаются в рамках процесса компилятора, либо **csc.exe** или **vbc.exe**, и выполнения анализа при построении проекта. Анализатор результаты выводятся вместе с результатами компилятора.

> [!NOTE]
> Вы также можете [установить анализаторы FxCop как расширение Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). В этом случае анализаторы выполняются, как вы вводите в редакторе кода, но они не выполняются во время сборки. Если вы хотите запустить анализаторы FxCop как часть непрерывной интеграции (CI), установите их как пакет NuGet вместо этого.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Выполняется ли команда выполнить анализ кода анализаторы FxCop?

Нет. При выборе **анализ** > **выполнить анализ кода** в Visual Studio 2017, он выполняет статический анализ кода или устаревших FxCop. **Запустить анализ кода** не оказывает влияния на анализаторы на основе Roslyn, включая анализаторы FxCop на базе Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Выполняется ли свойство проекта msbuild RunCodeAnalysis анализаторы?

Нет. **RunCodeAnalysis** свойство в файле проекта (например, *.csproj*) используется только для выполнения предыдущих версий FxCop. Он запускает задачу после сборки msbuild, которая вызывает **FxCopCmd.exe**. Это эквивалентно выбору **анализ** > **выполнить анализ кода** в Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Так как затем запустить анализаторы FxCop?

Чтобы запустить анализаторы FxCop, сначала [установите пакет NuGet](install-fxcop-analyzers.md) для них. Затем создайте проект или решение из Visual Studio или с помощью msbuild. Предупреждения и ошибки, которые создают анализаторы FxCop будет отображаться в **список ошибок** или окне командной строки.

## <a name="see-also"></a>См. также

- [Обзор анализаторов .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Начало работы с анализаторами](fxcop-analyzers.yml)
- [Установка анализаторы FxCop](install-fxcop-analyzers.md)
