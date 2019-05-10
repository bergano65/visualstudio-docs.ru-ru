---
title: Установка анализаторов FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 920e74b547bba97a742b68ceb057a0719d6ef700
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65459155"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Установка анализаторы FxCop в Visual Studio

Корпорация Майкрософт создала набор анализаторы, вызывается [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), содержащий наиболее важные правила «FxCop» из статического анализа кода, преобразуется в анализаторов Roslyn. Эти анализаторы проверьте код безопасности, производительности и проблемы проектирования, среди прочего.

Эти анализаторы FxCop можно установить как пакет NuGet или как расширение VSIX для Visual Studio. Дополнительные сведения о преимущества и недостатки каждого из них, см. в разделе [vs пакета NuGet. Расширение VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Чтобы установить анализаторы FxCop в виде пакета NuGet

1. [Определить, какая версия пакета анализатора](#fxcopanalyzers-package-versions) для установки, на основе вашей версии Visual Studio.

2. Установка пакета в Visual Studio, с помощью [консоль диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательский Интерфейс диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Страница nuget.org для каждого пакета анализатора показывает команду, чтобы вставить в **консоль диспетчера пакетов**. Есть даже под рукой кнопку, чтобы скопировать текст в буфер обмена.
   >
   > ![Страница NuGet.org команды консоли диспетчера пакетов](media/nuget-package-manager-command.png)

   Анализатор сборки устанавливаются, и они отображаются в **обозревателе решений** под **ссылки** > **анализаторы**.

   ![Анализаторы узел в обозревателе решений](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Версии пакетов FxCopAnalyzers

Чтобы определить, какая версия пакета анализаторы FxCop для установки для вашей версии Visual Studio, следуйте приведенным ниже рекомендациям:

| Версия Visual Studio | Версия пакета анализатора FxCop |
| - | - |
| Visual Studio 2017 версии 15,8 и более поздние версии | [2.9.2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.2) |
| Visual Studio 2017 версии 15.5 для версии 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 версии 15.3 для 15.4 | [2.3.0-Beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 версии 15.0 для 15.2 | [2.0.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 с обновлением 2 и 3 | [1.2.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 с обновлением 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Чтобы установить анализаторы FxCop как VSIX

::: moniker range="vs-2017"

В Visual Studio 2017 версии 15.5 и более поздних версий, можно установить [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) расширение, которое содержит все анализаторы FxCop для управляемых проектов.

1. В Visual Studio выберите **средства** > **расширения и обновления**.

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Кроме того, чтобы скачать расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Разверните **Online** в левой области, а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите «анализ кода» и проверьте наличие **Microsoft Code Analysis 2017** расширения.

   ![Расширение Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) расширения содержит все анализаторы FxCop для управляемых проектов. Чтобы установить это расширение:

1. В Visual Studio выберите **расширения** > **Управление расширениями**.

   **Управление расширениями** откроется диалоговое окно.

   > [!NOTE]
   > Кроме того, чтобы скачать расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Разверните **Online** в левой области, а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите «анализ кода» и проверьте наличие **Microsoft Code Analysis 2019** расширения.

   ![Расширение Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Выберите **загрузить**.

   Расширение загружается.

5. Выберите **ОК** чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio для запуска **установщик VSIX**.

   **Установщик VSIX** откроется диалоговое окно.

   ::: moniker range="vs-2017"

   ![Установщик VSIX для анализа кода Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Выберите **изменить** чтобы начать установку.

   После одну-две минуты не завершит установку.

7. Выберите **закрыть**, затем снова откройте Visual Studio.

::: moniker range="vs-2017"

Если вы хотите проверить, является ли расширение установлена, выберите **средства** > **расширения и обновления**. В **расширения и обновления** выберите **установленные** категории слева и выполните поиск расширения по имени.

::: moniker-end

::: moniker range=">=vs-2019"

Если вы хотите проверить, является ли расширение установлена, выберите **расширения** > **Управление расширениями**. В **Управление расширениями** выберите **установленные** категории слева и выполните поиск расширения по имени.

::: moniker-end

## <a name="see-also"></a>См. также

- [Обзор анализаторов Roslyn в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Использование анализаторов Roslyn в Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Перенос из FxCop для анализаторов Roslyn](../code-quality/fxcop-analyzers.yml)
