---
title: Установите сторонние анализаторы
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9da78f4c8e76f4e5b79f4cbdb0739d34fc465330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89091455"
---
# <a name="install-third-party-analyzers"></a>Установка сторонних анализаторов

Visual Studio включает в себя базовый набор анализаторов .NET Compiler Platform (*Roslyn*). Эти анализаторы всегда включены. Дополнительные анализаторы можно установить как в виде пакетов NuGet, так и в виде расширений Visual Studio в *VSIX* Files.

## <a name="to-install-nuget-analyzer-packages"></a>Установка пакетов анализатора NuGet

1. Найдите пакет анализатора, который вы хотите установить на www.nuget.org.

   Например, можно установить [StyleCop. Analyzers](https://www.nuget.org/packages/stylecop.analyzers/) для поиска проблем с стилями в базе кода.

2. Установите пакет в Visual Studio с помощью [консоли диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательского интерфейса диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > На странице www.nuget.org для каждого пакета анализатора отображается команда для вставки в **консоль диспетчера пакетов**. Существует даже удобная кнопка для копирования текста в буфер обмена.

   Сборки анализатора устанавливаются и отображаются в **Обозреватель решений** в **References**разделе  >  **анализаторы**ссылок.

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

3. В поле поиска введите имя расширения анализатора, которое требуется установить. Например, можно [установить анализаторы Microsoft FxCop](install-fxcop-analyzers.md#vsix) для проверки кода на наличие проблем безопасности и производительности, а также для других пользователей.

4. Нажмите кнопку **Скачать**.

   Расширение скачивается.

5. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio, чтобы запустить **установщик VSIX**.

   Откроется диалоговое окно **установщик VSIX** .

   ![Установщик VSIX для анализа кода Майкрософт](media/vsix-installer-code-analysis.png)

6. Нажмите кнопку **изменить** , чтобы начать установку.

7. Через одну или две минуты установка завершается. Щелкните **Закрыть**.

8. Снова откройте Visual Studio.

::: moniker range="vs-2017"

Если вы хотите проверить, установлено ли расширение, выберите **инструменты**  >  **расширения и обновления**. В диалоговом окне **расширения и обновления** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

::: moniker range=">=vs-2019"

Если требуется проверить, установлено ли расширение, выберите **расширения**  >  **Управление расширениями**. В диалоговом окне **Управление расширениями** выберите категорию **установленные** слева и найдите расширение по имени.

::: moniker-end

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Использование анализаторов кода в Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>См. также раздел

- [Обзор анализаторов кода в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Установка анализаторов FxCop](../code-quality/install-fxcop-analyzers.md)
