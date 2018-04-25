---
title: Установить анализаторы Roslyn в Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8a3b40b3b471e6bb57da561ac51f23086a0f01bd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="install-net-compiler-platform-analyzers"></a>Установить анализаторы платформой компилятора .NET

Visual Studio 2017 г. включает в себя базовый набор платформой компилятора .NET (*Roslyn*) анализаторов. Следующие анализаторы всегда активны. Можно установить дополнительные анализаторы как пакеты NuGet или расширения Visual Studio в *VSIX* файлов.

## <a name="to-install-nuget-package-analyzers"></a>Чтобы установить анализаторы пакета NuGet

1. [Определить, какую версию пакета анализатора](https://github.com/dotnet/roslyn-analyzers#recommended-version-of-analyzer-packages) для установки, на основе используемой версии Visual Studio.

1. Пакет будет установлен в Visual Studio, с помощью [консоль диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Страница nuget.org для каждого пакета анализатора показывает команду, чтобы вставить в **консоль диспетчера пакетов**. Имеется даже под рукой кнопку, чтобы скопировать текст в буфер обмена.
   >
   > ![Страница NuGet.org команда консоли диспетчера пакетов](media/nuget-package-manager-command.png)

   Анализатор сборки устанавливаются и отображаются в **обозревателе решений** под **ссылки** > **анализаторы**.

   ![Анализаторы узел в обозревателе решений](media/solution-explorer-analyzers-node.png)

## <a name="to-install-vsix-analyzers"></a>Чтобы установить анализаторы VSIX

1. В Visual Studio, выберите **средства** > **расширения и обновления**.

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Можно также загрузить расширения непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

1. Разверните **Online** в левой области, а затем выберите **Visual Studio Marketplace**.

1. В поле поиска введите «анализ кода» и найдите **2017 г. анализ кода Microsoft** расширения.

   ![Расширения Microsoft анализа кода](media/extensions-and-updates-code-analysis.png)

1. Выберите **загрузить**.

   Модуль загружается.

1. Выберите **ОК** , чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio для запуска **установщик VSIX**.

   **Установщик VSIX** откроется диалоговое окно.

   ![Установщик VSIX для анализа кода Microsoft](media/vsix-installer-code-analysis.png)

1. Выберите **изменить** чтобы начать установку.

1. После одну-две минуты завершения установки. Выберите **закрыть**.

1. Снова откройте Visual Studio.

Если вы хотите проверить, является ли модуль установлена, выберите **средства** > **расширения и обновления**. В **расширения и обновления** выберите **установленные** категории слева и выполните поиск расширение по имени.

## <a name="next-steps"></a>Следующие шаги

- [Используйте анализаторы Roslyn в Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>См. также

- [Общие сведения о анализаторы Roslyn в Visual Studio](../code-quality/roslyn-analyzers-overview.md)