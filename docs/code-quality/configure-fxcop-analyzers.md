---
title: Настройка анализаторов качества кода .NET с помощью editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fbd30859c5ee3dbbea80c6d88d68c0211da62c88
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706585"
---
# <a name="configure-net-code-quality-analyzers"></a>Настройка анализаторов качества кода .NET

Для некоторых анализаторов качества кода .NET (тех, которые начинаются с идентификаторов правил `CA` ) можно уточнить, к каким частям базы кода они должны применяться, с помощью [настраиваемых параметров](fxcop-analyzer-options.md). Каждый параметр указывается путем добавления пары "ключ-значение" в файл [EditorConfig](https://editorconfig.org) . Файл конфигурации может быть специфичным для файла, проекта, решения или всего репозитория.

> [!TIP]
> Добавьте в проект файл. editorconfig, щелкнув правой кнопкой мыши проект в **Обозреватель решений** и выбрав пункт **Добавить**  >  **новый элемент**. В окне **Добавление нового элемента** введите **editorconfig** в поле поиска. Выберите шаблон **Editorconfig File (по умолчанию)** и нажмите кнопку **Добавить**.
>
> ![Добавление файла editorconfig в проект в Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Сведения о настройке серьезности правила (например, о том, является ли это сообщение ошибкой или предупреждением) см. [в разделе Установка серьезности правила в файле EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Также можно выбрать один из встроенных [файлов или наборов правил EditorConfig](analyzer-rule-sets.md) , чтобы быстро включить или отключить категорию правил.

::: moniker-end

Оставшаяся часть этой статьи посвящена общему синтаксису для [вариантов, позволяющих уточнить,](fxcop-analyzer-options.md) где применяются анализаторы качества кода .NET.

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

Конфигурацию анализатора на основе EditorConfig можно включить для следующих областей:

- Конкретные документы
- Определенные папки
- Конкретные проекты
- Конкретные решения
- Весь репозиторий

Чтобы включить конфигурацию, добавьте файл с *расширением editorconfig* с параметрами в соответствующем каталоге. Этот файл также может содержать записи конфигурации серьезности диагностики на основе EditorConfig. Подробнее см. [здесь](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>См. также статью

- [Параметры области правил для анализаторов качества кода .NET](fxcop-analyzer-options.md)
- [Конфигурация анализатора](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Соглашения о написании кода .NET для EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
