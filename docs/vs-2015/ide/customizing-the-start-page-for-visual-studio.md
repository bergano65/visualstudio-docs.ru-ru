---
title: Настройка начальной страницы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd47441a0e9b1c97851aa8a6acac712c51a4493a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062936"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Настройка начальной страницы в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует несколько способов настройки начальной страницы Visual Studio: например, для этого можно использовать диалоговое окно **Открытие проекта** или открыть решение, загруженное последним. Также можно отобразить настраиваемую начальную страницу, т. е. страницу XAML Windows Presentation Foundation (WPF), которая открывается в окне инструментов и может использоваться для выполнения внутренних команд Visual Studio.

## <a name="customizing-the-default-start-page"></a>Настройка начальной страницы по умолчанию

1. В строке меню выберите **Сервис**, **Параметры**.

2. Разверните меню **Среда** и выберите **Запуск**.

3. В списке **При запуске** выберите элемент, который требуется настроить.

## <a name="show-a-custom-start-page"></a>Отображение настраиваемой начальной страницы

1. Установите настраиваемую начальную страницу одним из следующих способов:

    - Установите эту страницу из [Visual Studio Marketplace](https://marketplace.visualstudio.com/), с другого веб-сайта или со страницы своей локальной интрасети.

        > [!NOTE]
        >  Если вы предпочитаете страницу, предназначенную для более ранней версии Visual Studio, то можете обновить ее при помощи пакета SDK для Visual Studio. См. [Практическое руководство. Обновление настраиваемой начальной страницы Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Откройте файл VSIX, содержащий настраиваемую начальную страницу, или скопируйте и вставьте файлы начальной страницы в папку **%USERPROFILE% \Мои документы\Visual Studio 2015\StartPages** на компьютере.

    - Создайте собственную начальную страницу, если на вашем компьютере установлен пакет SDK для Visual Studio.

         Подробнее см. о [создании собственной начальной страницы](../misc/creating-your-own-start-page.md).

2. В строке меню выберите **Сервис**, **Параметры**.

3. Разверните меню **Среда** и выберите **Запуск**.

4. В списке **Настроить начальную страницу** выберите нужную страницу.

> [!NOTE]
>  Если ошибка в настраиваемой начальной странице вызывает сбой Visual Studio, можно запустить Visual Studio в безопасном режиме, а затем настроить использование начальной страницы по умолчанию. См. раздел [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>См. также раздел
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Создание собственной начальной страницы](../misc/creating-your-own-start-page.md)
