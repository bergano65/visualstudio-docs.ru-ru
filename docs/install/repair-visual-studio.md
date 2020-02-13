---
title: Восстановление Visual Studio
titleSuffix: ''
description: Сведения о восстановлении установки Visual Studio 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 368ca6619a2fcff48cc3bcc7eb70913247b631b2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114745"
---
# <a name="repair-visual-studio"></a>Восстановление Visual Studio

::: moniker range="vs-2017"

Иногда установка Visual Studio может повреждаться. В этом случае ее следует восстановить.

1. Найдите **Visual Studio Installer** на своем компьютере.

     Например, на компьютере с юбилейным обновлением или более поздней версией Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

   > [!NOTE]
   > На некоторых компьютерах установщик Visual Studio может быть указан под буквой **"M"**  — для **Microsoft Visual Studio**.
   >
   > Кроме того, Visual Studio Installer можно найти в следующем расположении: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Откройте установщик, выберите **Дополнительно** и **Восстановить**.

    ![Восстановление Visual Studio из Visual Studio Installer](media/repair-visual-studio.png "Восстановление Visual Studio из Visual Studio Installer")

   > [!NOTE]
   > При восстановлении Visual Studio среда будет сброшена. Локальные настройки, включая пользовательские расширения, установленные без повышения прав, параметры пользователя и профили, будут удалены. Ваши синхронизированные параметры, такие как темы, цвета и сочетания клавиш, будут восстановлены.
   >

   > [!TIP]
   > Параметр **Восстановить** отображается только для установленных экземпляров Visual Studio. Если вы не видите параметр **Восстановить**, скорее всего, что вы выбрали пункт **Дополнительно** в версии, которая указана в Visual Studio Installer как доступная вместо установленной.

::: moniker-end

::: moniker range="vs-2019"

1. Найдите установщик Visual Studio на своем компьютере.

     Например, на компьютере с Windows 10 нажмите кнопку **Пуск** и прокрутите список до буквы **V**, где расположен пункт **Visual Studio Installer**.

     ![Открытие Visual Studio Installer](media/vs-2019/vs-installer-windows-start.png "Открытие Visual Studio Installer")

     > [!NOTE]
     > Кроме того, Visual Studio Installer можно найти в следующем расположении:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Для продолжения работы может потребоваться обновление самого установщика. Если это так, следуйте инструкциям на экране.

1. В установщике найдите установленный у вас выпуск Visual Studio. Затем выберите **Дополнительно** и **Восстановить**.

     ![Восстановление Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Восстановление Visual Studio 2019")

   > [!NOTE]
   > При восстановлении Visual Studio среда будет сброшена. Локальные настройки, включая пользовательские расширения, установленные без повышения прав, параметры пользователя и профили, будут удалены. Ваши синхронизированные параметры, такие как темы, цвета и сочетания клавиш, будут восстановлены.
   >

   > [!TIP]
   > Параметр **Восстановить** отображается только для установленных экземпляров Visual Studio. Если вы не видите параметр **Восстановить**, скорее всего, что вы выбрали пункт **Дополнительно** в версии, которая указана в Visual Studio Installer как доступная вместо установленной.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Обновление Visual Studio](update-visual-studio.md)
* [Удаление Visual Studio](uninstall-visual-studio.md)
* [Устранение неполадок при установке и обновлении Visual Studio](troubleshooting-installation-issues.md)
