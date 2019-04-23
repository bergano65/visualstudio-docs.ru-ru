---
title: Изменение Visual Studio
titleSuffix: ''
description: Сведения о поэтапном изменении среды Visual Studio.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 03/30/2018
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a08a14d8d07248efdcac759852a38777745e9a51
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58789722"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Изменение Visual Studio путем добавления или удаления рабочих нагрузок и компонентов

::: moniker range="vs-2019"

Visual Studio можно легко изменить таким образом, чтобы она включала только необходимые компоненты и в нужное время. Для этого откройте Visual Studio Installer для добавления или удаления рабочих нагрузок и компонентов.

::: moniker-end

::: moniker range="vs-2017"

Мы упростили не только персонализацию Visual Studio в соответствии с выполняемыми задачами, но и настройку самой среды Visual Studio. Для этого запустите установщик Visual Studio и внесите нужные изменения.

::: moniker-end

Ниже описывается порядок действий.

## <a name="modify-workloads"></a>Изменение рабочих нагрузок

 Рабочие нагрузки содержат функции, которые требуются для используемого языка программирования или платформы. С помощью рабочих нагрузок можно изменить среду Visual Studio так, чтобы она поддерживала выполнение нужных задач в любое время.

>[!IMPORTANT]
>Чтобы установить, обновить или изменить среду Visual Studio, необходимо войти в учетную запись с правами администратора. Дополнительные сведения см. в разделе [Разрешения пользователей и Visual Studio](../ide/user-permissions-and-visual-studio.md).

::: moniker range="vs-2017"

1. Найдите установщик Visual Studio на своем компьютере.

     Например, на компьютере с Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

     ![Установщик Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Поиск установщика Microsoft Visual Studio")

     >[!NOTE]
     >На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"**  — для **Microsoft Visual Studio**.<br/><br/> Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Щелкните установщик (или коснитесь его), чтобы запустить, и выберите команду **Изменить**.

     ![Запустите или измените Visual Studio](media/modify-visual-studio.png "Изменение Visual Studio 2017")

     При наличии ожидающих обновлений кнопка "Изменить" будет находиться в другом месте. Таким образом, вы можете изменить Visual Studio без обновления, если захотите. Нажмите кнопку **Дополнительно**, затем кнопку **Изменить**.

     ![Обновление или изменение Visual Studio](media/modify-or-update-visual-studio.png "Обновление или изменение Visual Studio 2017")

1. На экране **Рабочие нагрузки** выберите рабочие нагрузки, которые нужно установить, или отмените выбор тех, которые нужно удалить.

    ![Диалоговое окно программы установки Visual Studio 2017](media/vs2017-modify-workloads.PNG "Выбор рабочей нагрузки в Visual Studio 2017")

1. Снова выберите команду **Изменить**.

1. После установки новых рабочих нагрузок и компонентов выберите команду **Запуск**.

::: moniker-end

::: moniker range="vs-2019"

1. Найдите установщик Visual Studio на своем компьютере.

     Например, на компьютере с Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

     ![Откройте Visual Studio Installer](media/vs2019-visual-studio-installer.png "Откройте Visual Studio Installer")

     > [!NOTE]
     > Кроме того, Visual Studio Installer можно найти в следующем расположении:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Для продолжения работы может потребоваться обновление самого установщика. Если это так, следуйте инструкциям на экране.

1. В установщике найдите установленный у вас выпуск Visual Studio и выберите **Изменить**.

     ![Обновление или изменение Visual Studio](media/vs-2019/vs-installer-modify.png "Обновление или изменение Visual Studio 2017")

1. На вкладке **Рабочие нагрузки** выберите рабочие нагрузки, которые нужно установить, или отмените выбор тех, которые нужно удалить.

    ![Диалоговое окно программы установки Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Выбор рабочей нагрузки в Visual Studio 2019")

1. Выберите, хотите ли вы принять параметр по умолчанию **Установить при скачивании** или параметр **Скачать все и установить**.

    ![Параметры установки Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Выбор установки при скачивании или установки после скачивания")

    Параметр "Скачать все и установить" удобен, если вы хотите сначала загрузить среду, а позже установить ее.

1. Выберите **Изменить**.

1. После установки новых рабочих нагрузок и компонентов выберите команду **Запуск** в Visual Studio Installer.

::: moniker-end

## <a name="modify-individual-components"></a>Изменение отдельных компонентов

Если вы не хотите устанавливать рабочие нагрузки для настройки установленного экземпляра Visual Studio, выберите в Visual Studio Installer вкладку **Отдельные компоненты**, затем включите нужные компоненты и следуйте указаниям.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Обновление Visual Studio](update-visual-studio.md)
* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
