---
title: Обновление Visual Studio
titleSuffix: ''
description: Пошаговые инструкции по обновлению Visual Studio до последней версии.
ms.date: 03/09/2019
ms.custom: seodec18
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e58927f434b5ad5b8d8fe34c29d034cfc4dd57dc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983979"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Обновление до последнего выпуска Visual Studio

::: moniker range="vs-2017"

Рекомендуем выполнить обновление до [последней версии](/visualstudio/releasenotes/vs2017-relnotes/) Visual Studio 2017, чтобы иметь доступ к новым компонентам, исправлениям и улучшениям.

И если вы хотите опробовать следующую версию, вы можете также скачать [релиз-кандидат](//visualstudio/releases/2019/release-notes/) Visual Studio 2019.

> [!IMPORTANT]
> Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в разделе [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Для Visual Studio для Mac см. раздел [Обновление Visual Studio для Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Visual Studio 2017 версии 15.6 или более поздней

Мы ускорили процесс установки и обновления, чтобы его можно выполнять непосредственно в интегрированной среде разработки. Вот как можно обновить версию 15.6 и более поздние версии до последней версии Visual Studio.

### <a name="use-the-notifications-hub"></a>Использование центра уведомлений

При наличии обновлений в Visual Studio отображается соответствующий флаг уведомления.

1. Сохраните все изменения.

1. Выберите флаг уведомления, чтобы открыть центр **уведомлений**, а затем выберите уведомление, которое вы хотите установить.

   ![Обновление Visual Studio 2017 с помощью центра уведомлений](media/vs-install-notifications-hub-15dot6.png "Центр уведомлений в Visual Studio 2017")

1. Когда откроется диалоговое окно **Обновление**, выберите **Обновить сейчас**.

    ![Обновление Visual Studio 2017 с помощью диалогового окна "Обновление" в центре уведомлений](media/vs-update-now-from-notifications-hub.png "Диалоговое окно \"Обновление\" в центре уведомлений в Visual Studio")

     Если откроется диалоговое окно управления доступом пользователя, выберите **Да**. Затем на некоторое время может открыться диалоговое окно с сообщением "Пожалуйста, подождите". Затем откроется Visual Studio Installer, чтобы начать обновление.

     ![Новый интерфейс Visual Studio Installer в версии 15.6](media/visual-studio-15dot6-installer.png "Новый интерфейс Visual Studio Installer в версии 15.6")

     Обновление продолжается. Когда обновление завершится, Visual Studio перезапустится.

     > [!NOTE]
     > Если вы запускаете Visual Studio с правами администратора, вручную перезапустите его после обновления.

### <a name="use-the-ide"></a>Использование интегрированной среды разработки

Можно проверить наличие обновлений и установить из в строке меню Visual Studio.

1. Сохраните все изменения.

1. Выберите **Справка** > **Проверка обновлений**.

     ![Новое меню "Справка" в Visual Studio версии 15.6](media/vs-help-menu-check-for-updates.png "Новое меню \"Справка\" в Visual Studio версии 15.6")

1. Когда откроется диалоговое окно **Обновление**, выберите **Обновить сейчас**.

   Как описано в предыдущем разделе, Visual Studio перезагружается после успешного завершения обновления.

   > [!NOTE]
   > Если вы запускаете Visual Studio с правами администратора, вручную перезапустите его после обновления.

### <a name="use-the-visual-studio-installer"></a>Использование Visual Studio Installer

Как и в предыдущих версиях Visual Studio, для установки обновлений можно использовать Visual Studio Installer.

1. Сохраните все изменения.

1. Запустите установщик. Прежде чем продолжить, может потребоваться обновить Visual Studio Installer.

   > [!NOTE]
   > На компьютере под управлением Windows 10 установщик можно найти в списке по букве **V** (**Установщик Visual Studio**) или по букве **M** (**Установщик Microsoft Visual Studio**).

1. На странице **Продукт** установщика найдите установленный у вас выпуск Visual Studio.

1. Если обновление доступно, вы увидите кнопку **Обновить**. (Поиск доступных обновлений может занять несколько секунд.)

   Чтобы установить обновления, нажмите кнопку **Обновить**.

     ![Обновление Visual Studio 2017 с помощью установщика Visual Studio](media/update-visual-studio.png "Обновление Visual Studio 2017 с помощью установщика Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Обновление Visual Studio 2017 версии 15.5 или более ранней версии

Если вы используете более раннюю версию, следуйте инструкциям ниже, чтобы применить обновление к Visual Studio 2017 версий 15.0–15.5.

### <a name="update-by-using-the-notifications-hub"></a>Обновление с помощью центра уведомлений

1. При наличии обновлений в Visual Studio отображается соответствующий флаг уведомления.

   ![Обновление Visual Studio 2017 с помощью центра уведомлений](media/notification-flag.png "Флажок уведомления об обновлении в Visual Studio")

   Выберите флажок уведомления, чтобы открыть **центр уведомлений**.

   ![Обновление Visual Studio 2017 с помощью центра уведомлений](media/notifications-hub.png "Центр уведомлений в Visual Studio")

1. Выберите уведомление **Доступно обновление Visual Studio**, чтобы открыть диалоговое окно **Расширения и обновления**.

   ![Обновление Visual Studio 2017 с помощью центра уведомлений](media/notifications-hub-select.png "Центр уведомлений в Visual Studio")

1. В диалоговом окне **Расширения и обновления** нажмите кнопку **Обновить**.

   ![Обновление Visual Studio 2017 с помощью центра уведомлений](media/notifications-extensions-and-updates.png "Диалоговое окно \"Расширения и обновления\" в Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Подробнее об уведомлениях Visual Studio

В Visual Studio выводятся уведомления о доступности обновления для самой среды Visual Studio или для любых ее компонентов, а также об определенных событиях в среде Visual Studio.

* Желтый цвет флажка уведомления означает, что доступно обновление Visual Studio для установки.
* Красный цвет флажка уведомления означает проблему с лицензией.
* Черный цвет флажка уведомления означает, что имеются дополнительные или информационные сообщения для просмотра.

Выберите флажок уведомления, чтобы открыть **центр уведомлений**, а затем выберите уведомления, в отношении которых необходимо предпринять меры. Уведомление можно также проигнорировать или закрыть.

 ![Просмотр дополнительного или информационного сообщения в центре уведомлений](media/notification-flag-optional.png "Флажок уведомления о дополнительном или информационном сообщении в Visual Studio")

Вы можете настроить пропуск уведомления, чтобы оно больше не отображалось в Visual Studio. Чтобы сбросить список игнорируемых уведомлений, нажмите кнопку **Параметры** в центре уведомлений.

   ![Нажатие кнопки "Параметры" в центре уведомлений для просмотра параметров уведомлений](media/vs-notifications-hub-settings-button.png "Нажатие кнопки \"Параметры\" в центре уведомлений для просмотра параметров уведомлений")

### <a name="update-by-using-the-visual-studio-installer"></a>Обновление с помощью установщика Visual Studio

1. Запустите установщик. Для продолжения работы может потребоваться обновление самого установщика. В этом случае появится соответствующий запрос.

   > [!NOTE]
   > На компьютере под управлением Windows 10 установщик можно найти в списке по букве **V** (**Установщик Visual Studio**) или по букве **M** (**Установщик Microsoft Visual Studio**).

1. На странице **Продукт** установщика найдите установленный у вас выпуск Visual Studio.

1. Если обновление доступно, вы увидите кнопку **Обновить**. (Поиск доступных обновлений может занять несколько секунд.)

   Чтобы установить обновления, нажмите кнопку **Обновить**.

     ![Обновление Visual Studio 2017 с помощью Visual Studio Installer](media/update-visual-studio.png "Обновление Visual Studio с помощью Visual Studio Installer")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Изменение Visual Studio](modify-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
* [Обновление Visual Studio для Mac](/visualstudio/mac/update)

::: moniker-end

::: moniker range="vs-2019"

Рекомендуем выполнить обновление до [последней версии](/visualstudio/releases/2019/release-notes/) Visual Studio 2019, чтобы иметь доступ к новым компонентам, исправлениям и улучшениям.

> [!IMPORTANT]
> Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в разделе [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Для Visual Studio для Mac см. раздел [Обновление Visual Studio для Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2019"></a>Обновление Visual Studio 2019

Вот как можно использовать Visual Studio Installer для обновления Visual&nbsp;Studio&nbsp;2019&nbsp; предварительной версии или Visual&nbsp;Studio&nbsp;2019&nbsp;, релиз-кандидат.

1. Запустите установщик.

     ![Откройте Visual Studio Installer](media/vs2019-visual-studio-installer.png "Откройте Visual Studio Installer")

   Для продолжения работы может потребоваться обновление самого установщика. Если это так, следуйте инструкциям на экране.

1. В установщике найдите установленный у вас выпуск Visual Studio.

   Например, если вы ранее установили Visual&nbsp;Studio Community&nbsp;2019&nbsp;, релиз-кандидат, и для него есть обновление, в установщике будет отображаться сообщение **Доступно обновление**.

     ![Выберите выпуск Visual Studio 2019, который вы хотите обновить](media/vs2019-update-visual-studio-community-rc.png "Выберите выпуск Visual Studio 2019, который вы хотите обновить")

1. Чтобы установить обновления, нажмите кнопку **Обновить**.

    ![Нажмите кнопку "Обновить", чтобы установить обновления](media/vs2019-choose-update-visual-studio-community-rc.png "Нажмите кнопку \"Обновить\", чтобы установить обновления")

1. После завершения обновления выберите **Запуск** для запуска Visual Studio.

    ![Выберите "Запуск", чтобы запустить Visual Studio](media/vs2019-choose-launch-visual-studio-community-rc.png "Выберите \"Запуск\", чтобы запустить Visual Studio")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Обновление Visual Studio для Mac](/visualstudio/mac/update)

::: moniker-end
