---
title: "Обновление сетевой установки Visual Studio | Документация Майкрософт"
description: "{{ЗАПОЛНИТЕЛЬ}}"
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
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
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Обновление сетевой установки Visual Studio

Вы можете обновлять макет сетевой установки Visual Studio до последних обновлений продуктов, что позволяет использовать его не только в качестве точки установки обновлений Visual Studio, но и для поддержки уже развернутых установок на клиентских рабочих станциях.

## <a name="how-to-update-a-network-layout"></a>Обновление сетевого макета
Чтобы обновить общий ресурс сетевой установки и разместить в ней последние обновления, выполните ту же команду `--layout`, которую вы использовали при первоначальном создании макета. Она выполнит инкрементное скачивание обновленных пакетов.

Если при первоначальном создании сетевого макета вы настроили частичный макет, обязательно используйте те же параметры командной строки, которые вы указали при создании макета сетевой установки (например, те же рабочие нагрузки и языковые параметры). Если вы укажете другие параметры, то повторный запуск команды `--layout` не обновит пакеты, не указанные в параметрах для этого запуска команды.

Если макет размещается на общем файловом ресурсе, мы рекомендуем сначала обновить локальную копию макета (например, `c:\vs2017offline`), и только после скачивания всех обновлений скопировать обновленные данные в общую папку (например, `\\server\products\VS2017`).  В противном случае повышается вероятность, что кто-то из пользователей запустит программу установки до завершения обновления макета и не сможет получить полное содержимое макета.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Как развернуть обновление на клиентских компьютерах
В зависимости от настроек сетевой среды обновление могут разворачивать администраторы предприятия или пользователи с клиентского компьютера. 

- Пользователи могут обновлять экземпляр Visual Studio, установленный из папки установки в автономном режиме.
  - Запустите установщик Visual Studio.
  - Нажмите кнопку **Обновить**.

- Администраторы могут обновлять клиентские развертывания Visual Studio без взаимодействия с пользователем, выполняя две отдельные команды.
  - Сначала нужно обновить установщик Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  - Теперь обновите само приложение Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Используйте [команду vswhere.exe](tools-for-managing-visual-studio-instances.md), чтобы узнать путь установки существующего экземпляра Visual Studio на клиентском компьютере.

> [!TIP]
> Дополнительные сведения о настройке уведомлений пользователям об обновлениях есть в статье [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Управление обновлениями для сетевых развертываний Visual Studio).


## <a name="see-also"></a>См. также
* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
* [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)

