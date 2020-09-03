---
title: Устаревший анализ управляемого кода
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18c4ebf61e7136d908ad1e444616b0af7ac59a48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238378"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Общие сведения об устаревшем анализе управляемого кода в Visual Studio

Visual Studio может выполнять анализ кода управляемого кода двумя способами: с [прежним анализом](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), также известным как статический анализ в виде FxCop для управляемых сборок, и с помощью современных [анализаторов кода](../code-quality/roslyn-analyzers-overview.md)на основе .NET Compiler Platform. В этом разделе рассматривается устаревший анализ. Дополнительные сведения об анализе кода на основе .NET Compiler Platform см. в статье [Обзор анализаторов на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md).

Анализ кода для управляемого кода анализирует управляемые сборки и сообщает сведения о сборках, например нарушения правил программирования и проектирования, заданных в [руководствах по проектированию .NET](/dotnet/standard/design-guidelines/).

Средство анализа представляет проводимые во время анализа проверки в виде предупреждающих сообщений. В предупреждающих сообщениях указываются все проблемы, связанные с программированием и разработкой, и, по возможности, сведения о методах их устранения.

> [!NOTE]
> Устаревший анализ (статический анализ кода) не поддерживается для проектов .NET Core и .NET Standard в Visual Studio. При выполнении анализа кода в проекте .NET Core или .NET Standard в составе MSBuild появится сообщение об ошибке, похожее на **ошибку: CA0055: не удалось определить платформу для \<your.dll> **. Для анализа кода в проектах .NET Core или .NET Standard используйте [анализаторы кода](../code-quality/roslyn-analyzers-overview.md) .

## <a name="ide-integrated-development-environment-integration"></a>Интеграция интегрированной среды разработки (IDE)

Вы можете выполнять анализ кода в проекте вручную или автоматически.

Для запуска анализа кода при каждом построении проекта выберите параметр на странице свойств **анализ кода** проекта. Дополнительные сведения см. [в разделе инструкции. Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Чтобы выполнить анализ кода в проекте вручную, в строке меню выберите **анализ**  >  **выполнение анализа кода**  >  **выполнить анализ \<project> кода **.

## <a name="rule-sets"></a>Наборы правил

Правила анализа управляемого кода группируются в [наборы правил](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Можно использовать один из стандартных наборов правил Майкрософт или [создать настраиваемый набор правил](../code-quality/how-to-create-a-custom-rule-set.md) для удовлетворения конкретной потребности.

## <a name="suppress-warnings"></a>Отключение предупреждений

Зачастую удобно указать, что предупреждение неприменимо. Это позволяет сообщить разработчику и другими лицам, которые, возможно, будут проверять код позже, что предупреждение рассмотрено и либо отложено, либо проигнорировано.

Подавление предупреждений в исходном виде реализуется с помощью настраиваемых атрибутов. Чтобы подавить предупреждение, добавьте атрибут `SuppressMessage` в исходный код, как показано в следующем примере:

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Дополнительные сведения см. в разделе [Отключение предупреждений](../code-quality/in-source-suppression-overview.md).

::: moniker range="vs-2017"

> [!NOTE]
> Если вы переносите проект в Visual Studio 2017, вы можете внезапно столкнуться с большим количеством предупреждений анализа кода. Если вы не готовы устранить предупреждения, их можно отключить, выбрав **анализировать**  >  **выполнение анализа кода и подавлять активные проблемы**.
>
> ![Выполнение анализа кода и отключение проблем в Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Если вы переносите проект в Visual Studio 2019, вы можете внезапно столкнуться с большим количеством предупреждений анализа кода. Если вы не готовы устранить предупреждения, их можно отключить, выбрав **анализировать**  >  **сборку и подавлять активные проблемы**.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Запуск анализа кода в рамках политики возврата

Каждая организация может предъявлять определенные требования к возвратам. В частности, может требоваться соблюдение следующих правил:

- В возвращенном коде нет ошибок сборки.

- Анализ кода выполняется как часть последней сборки.

Этого можно достичь, задав политики возврата. Дополнительные сведения см. [в разделе улучшение качества кода с помощью политик возврата проекта](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md).

## <a name="team-build-integration"></a>Интеграция Team Build

Существует возможность использования интегрированных возможностей системы построения для запуска средства анализа в рамках процесса построения. Дополнительные сведения см. в описании [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов на основе .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
- [Использование наборов правил для группировки правил анализа кода](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Практическое руководство. Включение и отключение автоматического анализа кода](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
