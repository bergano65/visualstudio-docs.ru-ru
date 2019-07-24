---
title: Настройка средств FxCop Analyzer с помощью editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0152ae9f76ea1318f717c41a70d3d46351c9021a
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300613"
---
# <a name="configure-fxcop-analyzers"></a>Настройка анализаторов FxCop

[Анализаторы FxCop](install-fxcop-analyzers.md) состоят из наиболее важных правил "FxCop" из статического анализа кода, преобразованных в анализаторы Roslyn. Настроить анализаторы кода FxCop можно двумя способами.

- С [набором правил](#fxcop-analyzer-rule-sets), который позволяет включить или отключить правило и задать серьезность нарушения индивидуальных правил.

- Начиная с версии 2.6.3 пакета NuGet [Microsoft. CodeAnalysis. фкскопанализерс](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) с помощью [editorconfig-файла](#editorconfig-file). [Настраиваемые параметры](fxcop-analyzer-options.md) позволяют уточнить, какие части базы кода следует анализировать.

> [!TIP]
> Сведения о различиях между анализом статического кода FxCop и анализаторами FxCop см. в статье [вопросы и ответы по FxCop Analyzer](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Наборы правил FxCop Analyzer

Одним из способов настройки анализаторов FxCop является использование *набора правил*XML. Набор правил — это группа правил анализа кода, которая определяет целевые проблемы и конкретные условия. Наборы правил позволяют включать и отключать правила, а также задавать уровень серьезности для отдельных нарушений правил.

Пакет NuGet анализатора FxCop включает предопределенные наборы правил для следующих категорий правил:

- разработка
- документация
- простота модификации
- именование
- производительность
- надежность
- безопасность
- использования

Дополнительные сведения см. в разделе [наборы правил для анализаторов Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Файл EditorConfig

Правила анализатора можно настроить, добавив пары "ключ-значение" в [editorconfig](https://editorconfig.org) -файл. Файл конфигурации может быть [специфичным для проекта](#per-project-configuration) или может [совместно](#shared-configuration) использоваться двумя или более проектами.

### <a name="per-project-configuration"></a>Конфигурация по проекту

Чтобы включить конфигурацию анализатора на основе editorconfig для конкретного проекта, добавьте *editorconfig* -файл в корневой каталог проекта.

> [!TIP]
> Вы можете добавить editorconfig-файл в проект, щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав **Добавить** > **новый элемент**. В окне **Добавление нового элемента** введите **editorconfig** в поле поиска. Выберите шаблон **Editorconfig File (по умолчанию)** и нажмите кнопку **Добавить**.
>
> ![Добавление элемента editorconfig в проект в Visual Studio](media/add-editorconfig-file.png)

В настоящее время отсутствует иерархическая поддержка для объединения editorconfig-файлов, которые существуют на разных уровнях каталогов, например на уровне решения и проекта.

### <a name="shared-configuration"></a>Общая конфигурация

Можно предоставить общий доступ к файлу editorconfig для конфигурации анализатора между двумя или более проектами, но для этого требуется выполнить некоторые дополнительные действия.

1. Сохраните *editorconfig* -файл в общем расположении.

2. Создайте файл *. props* со следующим содержимым:

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

3. Добавьте строку в *CSPROJ* -или *VBPROJ* -файл для импорта файла PROPS  , созданного на предыдущем шаге. Эту строку необходимо поместить перед любыми строками, которые импортируют файлы FxCop Analyzer *. props* . Например, если файл. props имеет имя *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Перезагрузите проект.

> [!NOTE]
> Нельзя настроить устаревшие правила FxCop (статический анализ кода FxCop) с помощью файла editorconfig.

## <a name="option-scopes"></a>Области параметров

Каждый параметр можно настроить для всех правил, для категории правил (например, именования или проектирования) или для конкретного правила.

### <a name="all-rules"></a>Все правила

Ниже приведен синтаксис для настройки параметра для всех правил.

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Категория правил

Для настройки параметра *категории* правил (например, именования, проектирования или производительности) используется следующий синтаксис:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. Рулекатегори. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Конкретное правило

Ниже приведен синтаксис для настройки параметра для конкретного правила.

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>См. также

- [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Анализаторы FxCop](install-fxcop-analyzers.md)
- [Соглашения о написании кода .NET для EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
