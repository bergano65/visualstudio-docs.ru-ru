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
ms.openlocfilehash: 182042db9a744d037e295a8448f8c49a9c7b3a97
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184800"
---
# <a name="configure-fxcop-analyzers"></a>Настройка анализаторов FxCop

[Пакет анализаторов FxCop](install-fxcop-analyzers.md) состоит из наиболее важных правил FXCop из устаревшего анализа, преобразованных в анализаторы кода на основе .NET Compiler Platform. Для некоторых правил FxCop можно уточнить, к каким частям базы кода следует применить эти параметры с помощью [настраиваемых параметров](fxcop-analyzer-options.md). Каждый параметр указывается путем добавления пары "ключ-значение" в файл [EditorConfig](https://editorconfig.org) . Файл конфигурации может быть [специфичным для проекта](#per-project-configuration) или может [совместно](#shared-configuration) использоваться двумя или более проектами.

> [!TIP]
> Добавьте в проект файл. editorconfig, щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав пункт **Добавить**  >  **новый элемент**. В окне **Добавление нового элемента** введите **editorconfig** в поле поиска. Выберите шаблон **Editorconfig File (по умолчанию)** и нажмите кнопку **Добавить**.
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

## <a name="enabling-editorconfig-based-configuration"></a>Включение конфигурации на основе Editorconfig

### <a name="vs2019-163-and-later--fxcopanalyzers-package-version-33x-and-later"></a>VS2019 16,3 и более поздних версий + Фкскопанализерс версии 3.3. x и более поздних версий

Конфигурацию анализатора на основе EditorConfig можно включить для следующих областей:

- Конкретные документы
- Определенные папки
- Конкретные проекты
- Конкретные решения
- Весь репозиторий

Чтобы включить конфигурацию, добавьте файл с *расширением editorconfig* с параметрами в соответствующем каталоге. Этот файл также может содержать записи конфигурации серьезности диагностики на основе EditorConfig. Дополнительные сведения см. [здесь](use-roslyn-analyzers.md#rule-severity).

### <a name="prior-to-vs2019-163-or-using-an-fxcopanalyzers-package-version-prior-to-33x"></a>До VS2019 16,3 или с помощью версии пакета Фкскопанализерс до 3.3. x

#### <a name="per-project-configuration"></a>Конфигурация по проекту

Чтобы включить конфигурацию анализатора на основе EditorConfig для конкретного проекта, добавьте *EditorConfig* -файл в корневой каталог проекта.

#### <a name="shared-configuration"></a>Конфигурация совместного использования

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

## <a name="see-also"></a>См. также статью

- [Параметры области действия правила для средств FxCop Analyzer](fxcop-analyzer-options.md)
- [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Анализаторы FXCop](install-fxcop-analyzers.md)
- [Соглашения о написании кода .NET для EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
