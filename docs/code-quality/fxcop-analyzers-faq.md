---
title: Анализ кода FxCop и анализаторы FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 83b9fb827ea413952713284073b712594fd26d52
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904959"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Часто задаваемые вопросы, посвященные FxCop и анализаторам FxCop

Разница между устаревшими функциями FxCop и анализаторами FxCop на первый взгляд может быть неочевидна. В этой статье будут раскрыты некоторые вопросы, которые могут возникать у вас.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>В чем разница между устаревшими функциями FxCop и анализаторами FxCop?

Устаревшие функции FxCop выполняют анализ после построения скомпилированной сборки. В этом случае запускается отдельный исполняемый файл **FxCopCmd.exe**. Средство FxCopCmd.exe загружает скомпилированную сборку, выполняет анализ кода и затем подготавливает отчет о результатах (или *данные диагностики*).

Анализаторы FxCop работают на основе .NET Compiler Platform (Roslyn). Они [устанавливаются в виде пакета NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package), на который задаются ссылки в проекте или решении. Анализаторы FxCop осуществляют анализ на основе исходного кода во время выполнения компилятора. Анализаторы FxCop размещаются в процессе компилятора (**csc.exe** или **vbc.exe**) и осуществляют анализ в процессе построения проекта. Результаты работы анализатора выводятся вместе с результатами выполнения компилятора.

> [!NOTE]
> Кроме того, вы можете [установить анализаторы FxCop в виде расширения Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). В этом случае анализаторы выполняются при вводе данных в редакторе кода и не применяются во время построения. Если вы хотите выполнять анализаторы FxCop в рамках процесса непрерывной интеграции, их следует устанавливать в виде пакета NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Запускаются ли анализаторы FxCop с помощью команды "Запустить анализ кода"?

Нет. Если выбрать команду **Анализ** > **Запустить анализ кода** в среде Visual Studio 2017, будет выполнен статический анализ кода (устаревшие функции FxCop). Команда **Запустить анализ кода** не применяется к анализаторам на основе платформы Roslyn, в том числе к анализаторам FxCop на основе Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Запускаются ли анализаторы с помощью свойства проекта msbuild RunCodeAnalysis?

Нет. Свойство **RunCodeAnalysis** в файле проекта (например, *.csproj*) используется только для выполнения устаревших функций FxCop. В этом случае после построения запускается задача msbuild, которая вызывает файл **FxCopCmd.exe**. Это эквивалентно выбору команды **Анализ** > **Запустить анализ кода** в среде Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Каким образом следует запускать анализаторы FxCop?

Для запуска анализаторов FxCop сначала необходимо [установить соответствующий пакет NuGet](install-fxcop-analyzers.md). После этого следует построить проект или решение из среды Visual Studio или с помощью msbuild. Возвращаемые анализаторами FxCop предупреждения и ошибки выводятся в **списке ошибок** или в окне командной строки.

## <a name="see-also"></a>См. также

- [Обзор анализаторов на платформе .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Начало работы с анализаторами](fxcop-analyzers.yml)
- [Установка анализаторов FxCop](install-fxcop-analyzers.md)
