---
title: Настройте анализаторы FxCop, с помощью editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816936"
---
# <a name="configure-fxcop-analyzers"></a>Настройте анализаторы FxCop

[Анализаторы FxCop](install-fxcop-analyzers.md) состоят из наиболее важных правила «FxCop» из статического анализа кода, преобразуется в анализаторов Roslyn. Анализаторы FxCop кода можно настроить двумя способами:

- С помощью [набор правил](#fxcop-analyzer-rule-sets), который позволяет включить или отключить правило и задать уровень серьезности нарушений отдельное правило.

- Начиная с версии 2.6.3 [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) пакетов NuGet, с помощью [editorconfig-файле](#editorconfig-file). [Настраиваемых параметров](fxcop-analyzer-options.md) позволяют уточнить какие части вашей базы кода для анализа.

> [!TIP]
> Сведения о различиях между FxCop статический анализ кода и анализаторы FxCop, см. в разделе [анализаторы FxCop часто задаваемые вопросы о](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Наборы правил FxCop анализатора

Для настройки анализаторы FxCop рекомендуется с помощью XML *набор правил*. Набор правил — это группа правил анализа кода, которые определяют целевые задачи и определенные условия. Наборы правил позволяют включить или отключить правило и задать уровень серьезности нарушений отдельное правило.

Пакет NuGet анализатора FxCop включает заранее заданные наборы правил для следующие категории правил:

- разработка
- документация
- простота модификации
- именование
- производительность
- надежность
- безопасность
- использования

Дополнительные сведения см. в разделе [наборов правил для анализаторов Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Файл EditorConfig

Можно настроить правила анализатора путем добавления пары "ключ значение" [.editorconfig](https://editorconfig.org) файла. Файл конфигурации может быть [для конкретного проекта](#per-project-configuration) или [общего](#shared-configuration) между двух или нескольких проектов.

### <a name="per-project-configuration"></a>Конфигурации отдельных проектов

Чтобы включить основе .editorconfig анализатора конфигурации для конкретного проекта, добавьте *.editorconfig* файл в корневой каталог проекта.

> [!TIP]
> Можно добавить файл editorconfig в проект, щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **добавить** > **новый элемент**. В **Добавление нового элемента** окне введите **editorconfig** в поле поиска. Выберите **editorconfig файла (по умолчанию)** шаблона и выберите **добавить**.
>
> ![Добавить элемент editorconfig в проект в Visual Studio](media/add-editorconfig-file.png)

В настоящее время не поддерживается иерархических для «объединение» .editorconfig файлы, которые существуют на уровнях другой каталог, например, на уровне решения и проекта.

### <a name="shared-configuration"></a>Общая конфигурация

Можно совместно использовать файл .editorconfig для анализатора конфигурации между двух или нескольких проектов, но он требует некоторых дополнительных шагов.

1. Сохранить *.editorconfig* файл в общую папку.

2. Создание *.props* файл со следующим содержимым:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Добавление строки в вашей *.csproj* или *.vbproj* файл для импорта *.props* файла, созданного на предыдущем шаге. Эта строка должны находиться перед всеми строками, импортировать анализаторе FxCop *.props* файлов. Например, если PROPS-файл называется *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Перезагрузите проект.

> [!NOTE]
> Устаревших правил FxCop (статического анализа кода FxCop) нельзя настроить с помощью файла с расширением editorconfig.

## <a name="option-scopes"></a>Параметр области

Каждый параметр можно настроить для всех правил, для категории правил (например, именования или проектирования) или для конкретного правила.

### <a name="all-rules"></a>Все правила

Синтаксис для настройки параметр для всех правил выглядит следующим образом:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. Имя_параметра = значение | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Категории правил

Синтаксис для настройки возможность *категории* правил (например, именования, конструктор или производительности) выглядит следующим образом:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Конкретное правило

Ниже приведен синтаксис для настройки параметр для конкретного правила:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>См. также

- [Analyzer configuration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Анализаторы FxCop](install-fxcop-analyzers.md)
