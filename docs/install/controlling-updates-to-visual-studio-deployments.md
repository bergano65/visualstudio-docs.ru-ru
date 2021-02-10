---
title: Управление обновлением развертываний
description: Узнайте, как изменить расположение, в котором Visual Studio ищет обновления при установке из сети.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ffa088de8852b0d5884cd4d9db5e65e1c179164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868547"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Управление обновлением сетевых развертываний Visual Studio

Администраторы предприятий часто создают макеты и размещают их на общих сетевых ресурсах, чтобы затем развертывать их для конечных пользователей.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Определение места, в котором Visual Studio будет искать обновления

По умолчанию Visual Studio продолжает искать обновления в Интернете, даже если установка была развернута из общей сетевой папки. Если обновление доступно, пользователь может установить его. Обновленное содержимое, которое не найдено в автономном макете, скачивается из Интернета.

Чтобы напрямую контролировать места, в которых Visual Studio выполняет поиск обновлений, можно изменить расположения для поиска. Также можно контролировать версию, до которой пользователи выполняют обновление. Для этого выполните следующие действия.

1. Создайте автономный макет.

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Скопируйте его в общую сетевую папку, в которой будете его размещать.

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Измените в этом макете файл response.json, указав для параметра `channelUri` значение, указывающее на управляемую администратором копию файла channelManifest.json.

   Не забудьте экранировать все символы обратной косой черты в этом значении, как показано в следующем примере:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Теперь конечные пользователи могут выполнять установку Visual Studio из этой папки.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Когда администратор предприятия решит, что нужно обновить установки пользователей до новой версии Visual Studio, ему нужно [обновить расположение макета](update-a-network-installation-of-visual-studio.md), разместив в нем обновленные файлы, как показано далее.

1. Используйте команду, аналогичную следующей:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Убедитесь, что файл response.json в обновленном макете содержит все измененные вами значения параметров, в частности channelUri:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Все существующие копии Visual Studio, установленные из этого макета, ищут обновления в `\\server\share\VS\ChannelManifest.json`. Если файл channelManifest.json новее, чем существующий в пользовательской установке, Visual Studio уведомит пользователя о наличии доступного обновления.

   Новые установки автоматически используют обновленную версию Visual Studio непосредственно из макета.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Управление уведомлениями в интегрированной среде разработки Visual Studio

::: moniker range="vs-2017"

Как описано выше, среда разработки Visual Studio проверяет расположение, из которого она была установлена (например, общую сетевую папку или Интернет), чтобы определить наличие доступных обновлений. Когда Visual Studio обнаруживает обновление, она уведомляет пользователя с помощью флага уведомления в правом верхнем углу окна.

   ![Флаг уведомления о наличии обновлений](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Как описано выше, среда разработки Visual Studio проверяет расположение, из которого она была установлена (например, общую сетевую папку или Интернет), чтобы определить наличие доступных обновлений. Когда Visual Studio обнаруживает обновление, она уведомляет пользователя с помощью значка уведомления в правом нижнем углу окна.

   ![Значок уведомления в Visual Studio IDE](media/vs-2019/notification-bar.png "Значок уведомления в IDE Visual Studio")

::: moniker-end

Если вы не хотите, чтобы конечные пользователи получали уведомления об обновлениях, уведомления можно отключить. (Например, может потребоваться отключить уведомления при доставке обновлений через централизованный механизм распространения программного обеспечения.)

::: moniker range="vs-2017"

Так как Visual Studio 2017 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет служебную программу `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Так как Visual Studio 2019 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет служебную программу `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Не забудьте заменить каталог в соответствии с установленным экземпляром, который нужно изменить.)

> [!TIP]
> Используйте [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) , чтобы найти определенный экземпляр Visual Studio на клиентской рабочей станции.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также раздел

* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для управления экземплярами Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
