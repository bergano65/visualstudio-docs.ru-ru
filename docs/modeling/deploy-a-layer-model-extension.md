---
title: Развертывание расширения модели слоев
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8fe915f31181af4158bdfe7e292313886ed7d4c
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983108"
---
# <a name="deploy-a-layer-model-extension"></a>Развертывание расширения модели слоев

Другие пользователи Visual Studio могут устанавливать расширения моделирования слоев, созданные вами с помощью Visual Studio.

## <a name="install-your-extension"></a>Установить расширение

Расширение скомпилировано в VSIX-файл, который можно устанавливать на других компьютерах. Кроме того, расширение можно установить на компьютере разработки, чтобы сделать его доступным в главном экземпляре Visual Studio.

### <a name="to-install-the-extension"></a>Установка расширения

1. В проекте, который содержит **source.vsix.manifest**откройте *bin* каталог в обозревателе файлов.

2. Копировать  **\*.vsix** файл на компьютер, на котором требуется установить расширение.

3. На конечном компьютере дважды щелкните VSIX-файл в проводнике.

    Откроется установщик VSIX.

### <a name="to-uninstall-the-extension"></a>Удаление расширения

::: moniker range="vs-2017"

1. В Visual Studio, выберите **средства** > **расширения и обновления**.

::: moniker-end

::: moniker range=">=vs-2019"

1. В Visual Studio, выберите **расширения** > **Управление расширениями**.

::: moniker-end

2. Щелкните имя расширения и нажмите кнопку **удаления**.

## <a name="install-an-extension-on-team-foundation-server"></a>Установить расширение на сервере Team Foundation Server

Серверы Team Foundation Server обычно не имеют установленной среды Visual Studio, и поэтому нельзя установить VSIX двойным щелчком. Необходимо вручную установить расширение.

### <a name="to-install-your-layer-extension-on-a-team-foundation-server-server"></a>Установка расширения слоев на сервере Team Foundation Server

1.  Копирования. *vsix* файлы с компьютера разработчика на компьютере Team Foundation Server (TFS).

     Поместите VSIX-файл в одно из указанных ниже мест.

    -   Установка для всех пользователей и служб:

         %ProgramFiles%\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft

    -   Установка только для сетевой службы, работающей сборки:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Если вы настроили сборки для выполнения в интерактивном режиме от имени определенного пользователя, можно установить только для этого пользователя:

         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

2.  Разверните каждый VSIX-файл в папке в том же местоположении.

    1.  Измените расширение имени файла с **.vsix** для **ZIP-файл**.

    2.  Извлеките содержимое ZIP-файла в папку.

    3.  Удалите ZIP-файл.

3.  Перезапустите TFS.
