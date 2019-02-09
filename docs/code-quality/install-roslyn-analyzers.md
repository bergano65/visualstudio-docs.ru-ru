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
ms.openlocfilehash: de4818a57dc09825e6f41a635ea777a9e3f06e2a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910515"
---
# <a name="install-net-compiler-platform-analyzers"></a>Установка анализаторов .NET Compiler Platform

Visual Studio 2017 включает в себя набор базовых платформы компилятора .NET (*Roslyn*) анализаторы. Эти анализаторы всегда включены. Можно установить дополнительные анализаторы как пакеты NuGet или расширения Visual Studio в *VSIX* файлов.

## <a name="to-install-nuget-analyzer-packages"></a>Чтобы установить пакеты NuGet анализатора

1. Найти пакет анализатора, который вы хотите установить на www.nuget.org. Например, может потребоваться [установить анализаторы Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) по проверке кода для проблем безопасности и производительности, среди прочего.

2. Установка пакета в Visual Studio, с помощью [консоль диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) или [пользовательский Интерфейс диспетчера пакетов](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Www.nuget.org страницы для каждого пакета анализатора показывает команду, чтобы вставить в **консоль диспетчера пакетов**. Есть даже под рукой кнопку, чтобы скопировать текст в буфер обмена.
   >
   > ![Страница NuGet.org команды консоли диспетчера пакетов](media/nuget-install-command.png)

   Сборки анализатора установлены и отображаются в **обозревателе решений** под **ссылки** > **анализаторы**.

## <a name="to-install-vsix-analyzers"></a>Чтобы установить VSIX анализаторы

1. В Visual Studio выберите **средства** > **расширения и обновления**.

   Появится диалоговое окно **Расширения и обновления**.

   > [!NOTE]
   > Кроме того, можно найти и загрузить анализатор расширения непосредственно из [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Разверните **Online** в левой области, а затем выберите **Visual Studio Marketplace**.

3. В поле поиска введите имя анализатора расширения, который вы хотите установить. Например, может потребоваться [установить анализаторы Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) по проверке кода для проблем безопасности и производительности, среди прочего.

4. Выберите **загрузить**.

   Расширение загружается.

5. Выберите **ОК** чтобы закрыть диалоговое окно, а затем закройте все экземпляры Visual Studio для запуска **установщик VSIX**.

   **Установщик VSIX** откроется диалоговое окно.

   ![Установщик VSIX для анализа кода Microsoft](media/vsix-installer-code-analysis.png)

6. Выберите **изменить** чтобы начать установку.

7. После одну-две минуты не завершит установку. Выберите **закрыть**.

8. Снова откройте Visual Studio.

Если вы хотите проверить, является ли расширение установлена, выберите **средства** > **расширения и обновления**. В **расширения и обновления** выберите **установленные** категории слева и выполните поиск расширения по имени.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Использование анализаторов Roslyn в Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>См. также

- [Обзор анализаторов Roslyn в Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Установка анализаторов FxCop](../code-quality/install-fxcop-analyzers.md)