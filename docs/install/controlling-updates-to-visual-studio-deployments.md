---
title: "Управление обновлением развертываний Visual Studio | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Управление обновлением сетевых развертываний Visual Studio

Администраторы предприятий часто создают макеты и размещают их на общих сетевых ресурсах, чтобы затем развертывать их для конечных пользователей.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Определение места, в котором Visual Studio будет искать обновления
По умолчанию Visual Studio продолжает искать обновления в Интернете, даже если установка была развернута из общей сетевой папки. Если существует обновление, пользователь сможет установить его. Из Интернета можно скачать любое обновленное содержимое, которое не доступно в макете автономной установки.

Если вы предпочитаете самостоятельно определять, где Visual Studio будет искать обновления и какие версии будут установлены для ваших пользователей, вы можете изменить расположение, в котором Visual Studio выполняет поиск обновлений. Для этого выполните следующие действия.

 1. Создайте автономный макет.
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Скопируйте его в общую сетевую папку, в которой будете его размещать.
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Измените в этом макете файл response.json, указав для параметра `channelUri` значение, указывающее на управляемую администратором копию файла channelManifest.json. <b>Примечание.</b> Не забудьте экранировать все символы обратной косой черты в этом значении, как показано в этом примере:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Теперь конечные пользователи могут выполнять установку Visual Studio из этой папки.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Когда администратор предприятия решит, что нужно обновить установки пользователей до новой версии Visual Studio, ему нужно [обновить расположение макета](update-a-network-installation-of-visual-studio.md), разместив в нем обновленные файлы с помощью следующей команды:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Убедитесь, что файл response.json в обновленном макете содержит все измененные вами значения параметров, в частности channelUri:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Все существующие копии Visual Studio, установленные из этого макета, будут искать обновления в `\\server\share\VS2017\ChannelManifest.json`. Если этот файл channelManifest.json новее, чем существующий в пользовательской установке, Visual Studio уведомит пользователя о наличии доступного обновления.
 8. Новые установки автоматически используют обновленную версию Visual Studio, сохраненную в макете.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Управление уведомлениями в интегрированной среде разработки Visual Studio
Как описано выше, среда разработки Visual Studio проверяет расположение, из которого она была установлена (общую сетевую папку или Интернет), чтобы определить наличие доступных обновлений. Когда Visual Studio обнаруживает обновление, по умолчанию она уведомляет пользователя с помощью флага уведомления в правом верхнем углу окна: ![Флаг уведомления о наличии обновлений](media/notification-flag.png)

Если вы не хотите, чтобы конечные пользователи получали такие уведомления об обновлениях (например, если обновления вы предоставляете через централизованный механизм распространения программного обеспечения), эти уведомления можно отключить.

Поскольку Visual Studio 2017 [сохраняет параметры в частном реестре](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), вы не можете изменить реестр обычным способом. Но Visual Studio предоставляет команду `vsregedit.exe`, с помощью которой вы можете изменить параметры Visual Studio. Чтобы отключить уведомления, выполните следующую команду:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

В приведенной выше команде измените значение каталога так, чтобы она соответствовала тому установленному экземпляру, который нужно изменить. 

> [!TIP]
> Используйте [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) , чтобы найти определенный экземпляр Visual Studio на клиентской рабочей станции. 

## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для управления экземплярами Visual Studio](tools-for-managing-visual-studio-instances.md)

