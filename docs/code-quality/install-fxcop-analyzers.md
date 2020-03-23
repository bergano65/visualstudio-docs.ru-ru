---
title: Установка анализаторов FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508775"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Установка анализаторов FxCop в Visual Studio

Корпорация Майкрософт создала набор анализаторов, [называемых Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), который содержит наиболее важные правила "FxCop" из устаревшего анализа. Эти анализаторы проверяют ваш код на наличие проблем с безопасностью, производительностью и дизайном.

Вы можете установить эти анализаторы FxCop либо в виде пакета NuGet, либо в качестве расширения VSIX в Visual Studio. Чтобы узнать о плюсах и минусах каждого из них, [см.](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)

## <a name="nuget-package"></a>Пакет NuGet

::: moniker range=">=vs-2019"

В Visual Studio 2019 версия 16.3 и позже, вы можете установить [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet пакет непосредственно из проекта код анализ свойств страницы:

1. Нажмите на узла проекта в **Solution Explorer,** выберите **свойства,** а затем выберите вкладку **Code Analysis.**

   ![Установка пакета анализаторов FxCop со страницы свойств в Visual Studio](media/install-fxcop-properties-page.png)

2. Нажмите кнопку **Установить**.

   Visual Studio устанавливает последнюю версию пакета Microsoft.CodeAnalysis.FxCopAnalyzers. Сборки отображаются в **Solution Explorer** под**анализаторами** **ссылок.** > 

   ![Узла анализаторов в Solution Explorer](media/solution-explorer-analyzers-node.png)

Если вы используете старую версию Visual Studio 2019, установите пакет с помощью [консоли package Manager](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [uI-пакета manager.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

::: moniker-end

::: moniker range="vs-2017"

1. [Определите, какой анализатор пакет версии](#fxcopanalyzers-package-versions) для установки, на основе вашей версии Visual Studio.

2. Установите пакет в Visual Studio с помощью [консоли менеджера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [uI-пакета manager.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

   > [!NOTE]
   > Страница nuget.org для каждого пакета анализатора показывает команду для вставки в **консоль менеджера пакетов.** Там даже удобная кнопка, чтобы скопировать текст на буфер обмена.
   >
   > ![NuGet.org странице, отображаев команду консоли менеджера пакетов](media/nuget-package-manager-command.png)

   Сборки анализатора установлены, и они появляются в **Solution Explorer** под **справочниками** > **анализаторов.**

::: moniker-end

### <a name="custom-installation"></a>Выборочная установка

Для пользовательской установки, например, чтобы указать другую версию пакета, выберите кнопку эллипсис (...) на странице анализа кода проекта. Эта кнопка открывает менеджер пакета NuGet с "Microsoft.CodeAnalysis.FxCopAnalyzers" в качестве строки поиска.

![Установите пользовательский пакет анализаторов FxCop со страницы свойств в Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> [Определите, какой анализатор пакет версии](#fxcopanalyzers-package-versions) для установки, на основе вашей версии Visual Studio. Вы также можете установить пакет из [uI-пакета Manager.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

### <a name="fxcopanalyzers-package-versions"></a>Версии пакетов FxCopAnalyzers

Используйте следующие рекомендации, чтобы определить, какую версию пакета анализаторов FxCop установить для вашей версии Visual Studio:

| Версия Visual Studio | Версия пакета анализаторов FxCop |
| - | - |
| Визуальная студия 2019 (все версии)<br />Визуальная студия 2017 версия 15.8 и более поздние | [Последнее](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Визуальная студия 2017 версия 15,5 до 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 версия 15.3 до 15.4 | [2.3.0-бета1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Визуальная студия 2017 версия 15.0 до 15.2 | [2.0.0-бета2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Визуальное обновление студии 2015 2 и 3 | [1.2.0-бета2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 с обновлением 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

На версии Visual Studio 2017 15.5 и позже можно установить расширение [Microsoft Code Analysis 2017,](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) содержащее все анализаторы FxCop для управляемых проектов.

1. В Visual Studio выберите **расширения и обновления инструментов.** **Tools** >

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Кроме того, загрузите расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Расширить **Интернет** в левом стеле, а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите "анализ кода" и ищите расширение **Microsoft Code Analysis 2017.**

   ![Расширение Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Расширение [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) содержит все анализаторы FxCop для управляемых проектов. Для установки этого расширения:

1. В Visual Studio выберите **расширения** > **Управления расширениями.**

   Открывается диалоговая коробка **«Управление расширениями».**

   > [!NOTE]
   > Кроме того, загрузите расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Расширить **Интернет** в левом стеле, а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите "анализ кода" и ищите расширение **Microsoft Code Analysis 2019.**

   ![Расширение Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Выберите **Скачать**.

   Расширение загружается.

5. Выберите **OK,** чтобы закрыть диалоговую коробку, а затем закрыть все экземпляры Visual Studio для запуска **VSIX Installer.**

   Открывается **диалоговая коробка VSIX Installer.**

   ::: moniker range="vs-2017"

   ![Установка VSIX для анализа кода Майкрософт](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Выберите **изменение** для начала установки.

   Через минуту или две установка завершается.

7. Выберите **Закрыть**, затем открыть Visual Studio снова.

::: moniker range="vs-2017"

Если вы хотите проверить, установлено ли расширение, выберите расширения**и обновления инструментов.** **Tools** >  В диалоговом окне **расширений и обновлений** выберите категорию **«Установлено»** слева, а затем ищите расширение по имени.

::: moniker-end

::: moniker range=">=vs-2019"

Если вы хотите проверить, установленли ли расширение, выберите **расширения Управления** > **расширениями.** В диалоговом окне **расширения управления** выберите категорию **«Установлено»** слева, а затем ищите расширение по имени.

::: moniker-end

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов кода в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Использование анализаторов кода в Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Переход от устаревшего анализа к анализатору кода](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
