---
title: Анализ кода FxCop и анализаторы FxCop
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431369"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Часто задаваемые вопросы, посвященные FxCop и анализаторам FxCop

Разница между устаревшими функциями FxCop и анализаторами FxCop на первый взгляд может быть неочевидна. В этой статье будут раскрыты некоторые вопросы, которые могут возникать у вас.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>В чем разница между устаревшими функциями FxCop и анализаторами FxCop?

Устаревшие функции FxCop выполняют анализ после построения скомпилированной сборки. В этом случае запускается отдельный исполняемый файл **FxCopCmd.exe**. Средство FxCopCmd.exe загружает скомпилированную сборку, выполняет анализ кода и затем подготавливает отчет о результатах (или *данные диагностики*).

Анализаторы FxCop работают на основе .NET Compiler Platform (Roslyn). Они [устанавливаются в виде пакета NuGet](install-fxcop-analyzers.md#nuget-package), на который задаются ссылки в проекте или решении. Анализаторы FxCop осуществляют анализ на основе исходного кода во время выполнения компилятора. Анализаторы FxCop размещаются в процессе компилятора (**csc.exe** или **vbc.exe**) и осуществляют анализ в процессе построения проекта. Результаты работы анализатора выводятся вместе с результатами выполнения компилятора.

> [!NOTE]
> Кроме того, вы можете [установить анализаторы FxCop в виде расширения Visual Studio](install-fxcop-analyzers.md#vsix). В этом случае анализаторы выполняются при вводе данных в редакторе кода и не применяются во время построения. Если вы хотите выполнять анализаторы FxCop в рамках процесса непрерывной интеграции, их следует устанавливать в виде пакета NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Запускаются ли анализаторы FxCop с помощью команды "Запустить анализ кода"?

До visual Studio 2019 16.5 релиз, когда вы выбираете **Анализ** > **запуска кода**, он выполняет устаревание анализа. Начиная Visual Studio 2019 16.5, Вариант меню **run Code Analysis** выполняет анализаторы на основе Roslyn для выбранного проекта или решения. Если вы установили анализаторы FxCop на основе Roslyn, они также будут выполнены. Для получения дополнительной информации [см. Как: Выполнить анализ кода вручную для управляемого кода](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Запускаются ли анализаторы с помощью свойства проекта msbuild RunCodeAnalysis?

Нет. Свойство **RunCodeAnalysis** в файле проекта (например, *.csproj*) используется только для выполнения устаревших функций FxCop. В этом случае после построения запускается задача msbuild, которая вызывает файл **FxCopCmd.exe**.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Каким образом следует запускать анализаторы FxCop?

Для запуска анализаторов FxCop сначала необходимо [установить соответствующий пакет NuGet](install-fxcop-analyzers.md). После этого следует построить проект или решение из среды Visual Studio или с помощью msbuild. Возвращаемые анализаторами FxCop предупреждения и ошибки выводятся в **списке ошибок** или в окне командной строки.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Я получаю предупреждение CA0507 даже после установки пакета NuGet анализаторов FxCop

Если вы установили анализаторы FxCop, но продолжаете получать предупреждение CA0507 **""Запуск анализа кода" был уволен в пользу анализаторов FxCop, которые работают во время сборки ",** возможно, потребуется установить **RunCodeAnalysis** msbuild собственности в [файле проекта](../ide/solutions-and-projects-in-visual-studio.md#project-file) **на ложные**. В противном случае анализ наследия будет выполняться после каждой сборки.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>Какие правила были перенесены на анализаторы FxCop?

Для получения информации о том, какие устаревшие правила [Fxcop rule port status](fxcop-rule-port-status.md)анализа были перенесены на [анализаторы FxCop,](install-fxcop-analyzers.md)см.

## <a name="code-analysis-warnings-are-treated-as-errors"></a>Предупреждения об анализе кода рассматриваются как ошибки

Если проект использует опцию сборки для обработки предупреждений как ошибок, предупреждения аналитика FxCop могут отображаться как ошибки. Чтобы предотвратить обработку предупреждений о анализе кода как ошибки, выполните последующие шаги в [часто задаваемых вопросов анализа кода.](../code-quality/analyzers-faq.md#treat-warnings-as-errors)

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов на платформе .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Переход на анализаторы FxCop](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [Установка анализаторов FxCop](install-fxcop-analyzers.md)
