---
title: Настройка средств FxCop Analyzer с помощью editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b1d178adbbb847b2629ee785a7a0fa4e990a46dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587723"
---
# <a name="configure-fxcop-analyzers"></a>Настройка анализаторов FxCop

[Пакет анализаторов FxCop](install-fxcop-analyzers.md) состоит из наиболее важных правил FXCop из устаревшего анализа, преобразованных в анализаторы кода на основе .NET Compiler Platform. Для некоторых правил FxCop можно уточнить, к каким частям базы кода следует применить эти параметры с помощью [настраиваемых параметров](fxcop-analyzer-options.md). Каждый параметр указывается путем добавления пары "ключ-значение" в файл [EditorConfig](https://editorconfig.org) . Файл конфигурации может быть [специфичным для проекта](#per-project-configuration) или может [совместно](#shared-configuration) использоваться двумя или более проектами.

> [!TIP]
> Добавьте в проект файл. editorconfig, щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав **Добавить** > **новый элемент**. В окне **Добавление нового элемента** введите **editorconfig** в поле поиска. Выберите шаблон **Editorconfig File (по умолчанию)** и нажмите кнопку **Добавить**.
>
> ![Добавление файла editorconfig в проект в Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Сведения о настройке серьезности правила (например, о том, является ли это сообщение ошибкой или предупреждением) см. [в разделе Установка серьезности правила в файле EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Также можно выбрать один из встроенных [файлов или наборов правил EditorConfig](analyzer-rule-sets.md) , чтобы быстро включить или отключить категорию правил.

::: moniker-end

Оставшаяся часть этой статьи посвящена общему синтаксису [параметров, которые точно определяют,](fxcop-analyzer-options.md) где применяются правила FXCop.

> [!NOTE]
> Старые правила FxCop нельзя настроить с помощью файла EditorConfig. Сведения о различиях между устаревшим анализом и анализаторами FxCop см. в статье [вопросы и ответы по FxCop Analyzer](fxcop-analyzers-faq.md).

## <a name="option-scopes"></a>Области параметров

Каждый вариант уточнения можно настроить для всех правил, для категории правил (например, именования или проектирования) или для конкретного правила.

### <a name="all-rules"></a>Все правила

Ниже приведен синтаксис для настройки параметра для *всех* правил.

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Категория правил

Для настройки параметра *категории* правил (например, именования, проектирования или производительности) используется следующий синтаксис:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. Рулекатегори. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Конкретное правило

Ниже приведен синтаксис для настройки параметра для *конкретного* правила.

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Конфигурация по проекту

Чтобы включить конфигурацию анализатора на основе EditorConfig для конкретного проекта, добавьте *EditorConfig* -файл в корневой каталог проекта.

В настоящее время отсутствует иерархическая поддержка для объединения editorconfig-файлов, которые существуют на разных уровнях каталогов, например на уровне решения и проекта.

## <a name="shared-configuration"></a>Конфигурация совместного использования

Вы можете предоставить общий доступ к файлу editorconfig для конфигурации анализатора FxCop между двумя или более проектами, но для этого требуется выполнить некоторые дополнительные действия.

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

3. Добавьте строку в *CSPROJ* -или *VBPROJ* -файл для импорта файла *PROPS* , созданного на предыдущем шаге. Эту строку необходимо поместить перед любыми строками, которые импортируют файлы FxCop Analyzer *. props* . Например, если файл. props имеет имя *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Перезагрузите проект.

> [!NOTE]
> Произвольное общее расположение файла EditorConfig, описанного здесь, применяется только для настройки области определенных правил анализатора FxCop. Для других параметров, таких как серьезность правила, общие параметры редактора и стиль кода, файл EditorConfig всегда должен быть помещен в папку проекта или в родительскую папку.

## <a name="see-also"></a>См. также:

- [Параметры области действия правила для средств FxCop Analyzer](fxcop-analyzer-options.md)
- [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Анализаторы FxCop](install-fxcop-analyzers.md)
- [Соглашения о написании кода .NET для EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
