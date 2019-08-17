---
title: Установка анализаторов Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 284f33d9d7af885958ed13101e1449edc5c8f2be
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551085"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>Установка .NET Compiler Platform анализаторов кода

Visual Studio включает в себя базовый набор анализаторов .NET Compiler Platform (*Roslyn*). Эти анализаторы всегда включены. Дополнительные анализаторы можно установить как в виде пакетов NuGet, так и в виде расширений Visual Studio в *VSIX* Files.

## <a name="to-install-nuget-analyzer-packages"></a>Установка пакетов анализатора NuGet

1. Найдите пакет анализатора, который вы хотите установить на www.nuget.org.

   Например, можно [установить анализаторы Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) для проверки кода на наличие проблем безопасности и производительности, а также для других пользователей. Или установите [стилекопанализерс](https://www.nuget.org/packages/stylecop.analyzers/) , чтобы найти проблемы с стилями в базе кода.

2. Установите пакет в Visual Studio с помощью [консоли диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > www.nuget.org страницы для каждого пакета анализатора показывает команду, чтобы вставить в **консоль диспетчера пакетов**. Существует даже удобная кнопка для копирования текста в буфер обмена.

   Сборки анализатора устанавливаются и отображаются в **Обозреватель решений** в разделе анализаторы **ссылок** > .

## <a name="to-install-vsix-analyzers"></a>Установка анализаторов VSIX

::: moniker range="vs-2017"

1. В Visual Studio выберите **инструменты** > **расширения и обновления**.

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Кроме того, вы можете найти и скачать расширение анализатора непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio выберите **расширения** > **Управление расширениями**.

   Откроется диалоговое окно **Управление расширениями** .

   > [!NOTE]
   > Кроме того, вы можете найти и скачать расширение анализатора непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. В левой области разверните узел в **сети** , а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите имя расширения анализатора, которое требуется установить. Например, можно [установить анализаторы Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) для проверки кода на наличие проблем безопасности и производительности, а также для других пользователей.

4. Выберите **скачать**.

   Расширение скачивается.

5. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio, чтобы запустить **установщик VSIX**.

   Откроется диалоговое окно **установщик VSIX** .

   ![Установщик VSIX для анализа кода Майкрософт](media/vsix-installer-code-analysis.png)

6. Нажмите кнопку **изменить** , чтобы начать установку.

7. Через одну или две минуты установка завершается. Нажмите кнопку **Закрыть**.

8. Снова откройте Visual Studio.

::: moniker range="vs-2017"

Если вы хотите проверить, установлено ли расширение, выберите **инструменты** > **расширения и обновления**. В диалоговом окне **расширения и обновления** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

::: moniker range=">=vs-2019"

Если требуется проверить, установлено ли расширение, выберите **расширения** > **Управление расширениями**. В диалоговом окне **Управление расширениями** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Использование анализаторов кода в Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>См. также

- [Обзор анализаторов кода в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Установка анализаторов FxCop](../code-quality/install-fxcop-analyzers.md)