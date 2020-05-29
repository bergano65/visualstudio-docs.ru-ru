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
ms.openlocfilehash: 06391a260909aba08d8c2d2aa9078f9c4383897e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182850"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Установка средств FxCop Analyzer в Visual Studio

Корпорация Майкрософт создала набор анализаторов, именуемый [Microsoft. CodeAnalysis. фкскопанализерс](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), который содержит наиболее важные правила FxCop из предыдущих версий. Эти анализаторы проверяют код на наличие проблем безопасности, производительности, проектирования и т. д.

Вы можете установить эти анализаторы FxCop либо как пакет NuGet, либо как расширение VSIX для Visual Studio. Дополнительные сведения о преимуществах и недостатках каждого из них см. в разделе [расширение пакетов NuGet и VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Пакет NuGet

::: moniker range=">=vs-2019"

В Visual Studio 16,3 2019 и более поздних версиях пакет NuGet [Microsoft. CodeAnalysis. фкскопанализерс](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) можно установить непосредственно на странице свойств анализа кода проекта:

1. Щелкните правой кнопкой мыши узел проекта в **Обозреватель решений**, выберите пункт **свойства**, а затем перейдите на вкладку **анализ кода** .

   ![Установка пакета FxCop Analyzer со страницы свойств в Visual Studio](media/install-fxcop-properties-page.png)

2. Нажмите кнопку **Установить**.

   Visual Studio устанавливает последнюю версию пакета Microsoft. CodeAnalysis. Фкскопанализерс. Сборки отображаются в **Обозреватель решений** в разделе **References**  >  **анализаторы**ссылок.

   ![Узел «Анализаторы» в обозреватель решений](media/solution-explorer-analyzers-node.png)

Если вы используете более раннюю версию Visual Studio 2019, установите пакет с помощью [консоли диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Определите версию пакета анализатора](#fxcopanalyzers-package-versions) для установки на основе вашей версии Visual Studio.

2. Установите пакет в Visual Studio с помощью [консоли диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > На странице nuget.org для каждого пакета анализатора отображается команда для вставки в **консоль диспетчера пакетов**. Существует даже удобная кнопка для копирования текста в буфер обмена.
   >
   > ![Страница NuGet.org с командой консоли диспетчера пакетов](media/nuget-package-manager-command.png)

   Сборки анализатора устанавливаются и отображаются в **Обозреватель решений** в разделе **References** > **анализаторы**ссылок.

::: moniker-end

### <a name="custom-installation"></a>Выборочная установка

Для выборочной установки, например для указания другой версии пакета, нажмите кнопку с многоточием (...) на странице свойств анализ кода проекта. Эта кнопка открывает диспетчер пакетов NuGet с именем Microsoft. CodeAnalysis. Фкскопанализерс в качестве строки поиска.

![Установить пользовательский пакет анализаторов FxCop со страницы "Свойства" в Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Определите [версию пакета анализатора](#fxcopanalyzers-package-versions) для установки на основе вашей версии Visual Studio. Пакет также можно установить из [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Версии пакетов Фкскопанализерс

Чтобы определить версию пакета средств FxCop Analyzer для установки в вашей версии Visual Studio, следуйте приведенным ниже рекомендациям.

| Версия Visual Studio | Версия пакета анализатора FxCop |
| - | - |
| Visual Studio 2019 (все версии) | [Актуальная](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) | 
| Visual Studio 2017 версии 15.9 | [2.9.9](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.9) |
| Visual Studio 2017 версии 15,5 до 15,8 | [2.6.4](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.4) |
| Visual Studio 2017 версии 15,3 до 15,4 | [2.3.0 — Beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 версии 15,0 до 15,2 | [2.0.0 — бета-версия](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 с обновлением 2 и 3 | [1.2.0 — бета-версия](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 с обновлением 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

В Visual Studio 2017 версии 15,5 и более поздних версиях можно установить расширение [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) , которое содержит все анализаторы FxCop для управляемых проектов.

1. В Visual Studio выберите **инструменты** > **расширения и обновления**.

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Также можно скачать расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. В левой области разверните узел в **сети** , а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите "анализ кода" и найдите расширение **Microsoft code analysis 2017** .

   ![Расширение Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

Расширение [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) содержит все анализаторы FxCop для управляемых проектов. Чтобы установить это расширение, выполните следующие действия.

1. В Visual Studio выберите **расширения** > **Управление расширениями**.

   Откроется диалоговое окно **Управление расширениями** .

   > [!NOTE]
   > Также можно скачать расширение непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. В левой области разверните узел в **сети** , а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите "анализ кода" и найдите расширение **Microsoft code analysis 2019** .

   ![Расширение Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Выберите **Скачать**.

   Расширение скачивается.

5. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio, чтобы запустить **установщик VSIX**.

   Откроется диалоговое окно **установщик VSIX** .

   ::: moniker range="vs-2017"

   ![Установщик VSIX для анализа кода Майкрософт](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Нажмите кнопку **изменить** , чтобы начать установку.

   Через одну или две минуты установка завершается.

7. Нажмите кнопку **Закрыть**, а затем снова откройте Visual Studio.

::: moniker range="vs-2017"

Если вы хотите проверить, установлено ли расширение, выберите **инструменты**  >  **расширения и обновления**. В диалоговом окне **расширения и обновления** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

::: moniker range=">=vs-2019"

Если требуется проверить, установлено ли расширение, выберите **расширения**  >  **Управление расширениями**. В диалоговом окне **Управление расширениями** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

## <a name="see-also"></a>См. также статью

- [Обзор анализаторов кода в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Использование анализаторов кода в Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Миграция из устаревшего анализа в анализаторы кода](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
