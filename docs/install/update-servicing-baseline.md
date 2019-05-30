---
title: Обновление Visual Studio во время обслуживания
titleSuffix: ''
description: Узнайте, как обновить Visual Studio, оставаясь на базовой версии.
ms.date: 05/22/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213785"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Обновление Visual Studio во время обслуживания

Visual Studio 2019 будет часто обновляться в ходе своего [жизненного цикла](/visualstudio/productinfo/release-rhythm.md#release-channel-updates). Это будут как промежуточные обновления (например, с версии 16.0 до версии 16.1), при которых будут добавляться новые функции и компоненты, так и служебные обновления (примером, с версии 16.0.4 до версии 16.0.5), когда вносятся только исправления известных серьезных проблем. 

Администраторы могут не выполнять промежуточные обновления своих клиентов, оставляя их на базовой версии, служебные обновления для которой продолжают выходить в течение года после выпуска следующей базовой версии. Это позволяет разработчикам и администраторам лучше адаптироваться к новым функциям, исправлениям ошибок и компонентам, добавляемым при промежуточных обновлениях. 16.0.x — это первая базовая версия. Дополнительные сведения см. в разделе [Варианты поддержки для клиентов уровня Enterprise и Professional](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Как установить базовую версию

Чтобы приступить к использованию базовой версии, скачайте начальный загрузчик Visual Studio Installer определенной версии Visual Studio на сайте [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). В таких загрузчиках приводятся ссылки на конфигурации, рабочие нагрузки и компоненты для определенной версии Visual Studio. 

> [!NOTE]
> Обратите внимание, что доступны как загрузчики определенной версии, так и обычные загрузчики. Обычные загрузчики настроены на использование последней доступной версии Visual Studio. В имени файла такого загрузчика, доступного для скачивания на my.visualstudio.com, присутствует номер (например, vs_enterprise__123456789 123456789.exe).

Во время установки администраторам необходимо настроить свои клиенты так, чтобы не выполнялось их обновление до последней версии. Это можно сделать, [изменив параметр channelUri в файле конфигурации ответов](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network), чтобы использовать манифест канала из макета или локальной папки, или [изменив channelUri при установке с помощью командной строки](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) или [настроив политики в системе клиента на отключение обновлений](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), чтобы предотвратить самостоятельное обновление клиентов. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Сетевая установка базовой версии

Администраторам, использующим макет сетевой установки, нужно изменить значение channelUri в `response.json` в макете, чтобы использовать файл channelmanifest.json, который находится в той же папке. Пошаговые инструкции см. в статье [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md). Если изменить параметр channelUri, клиенты будут искать обновления в расположении макета. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Установка базовой версии по Интернету

В случае установки по Интернету добавьте `--channelUri` с несуществующим манифестом канала с помощью командной строки при запуске установки. Это приведет к отключению в Visual Studio обновления до последней доступной версии. Пример:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Отключение обновления клиентов с помощью параметров политики

Другой вариант управления обновлениями клиента заключается в [отключении уведомлений об обновлениях](controlling-updates-to-visual-studio-deployments.md). Используйте этот вариант, если значение channelUri не было изменено при установке. Это не позволит клиенту получать ссылки на последнюю доступную версию. При этом все равно требуется начальный загрузчик определенной версии для обновления клиента до определенной версии.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Как оставаться на базовой версии

При выходе обновления для базовой версии на сайте [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0) публикуются файлы загрузчика определенной версии для служебного обновления. Существует несколько сценариев их использования.

При развертывании с помощью макета сетевой установки администратору потребуется обновить [расположение макета](update-a-network-installation-of-visual-studio.md). Клиенты, установленные из расположения, получат уведомления об обновлении. Если требуется развернуть обновление в клиентах, следуйте [этим инструкциям](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). При изменении файла response.json для обновления не добавляйте дополнительные рабочие нагрузки, компоненты или языки. Управление этими параметрами должно выполняться как "модифицирующее" развертывание после обновления продукта. 

В случае установки по Интернету запустите в клиенте новый начальный загрузчик определенной версии с параметром `--channelUri`, указывающим на манифест несуществующего канала. Если обновление развертывается в тихом или пассивном режиме, используйте две отдельные команды:

1. Сначала нужно обновить установщик Visual Studio: <br>```vs_enterprise.exe --quiet --update```
2. Теперь обновите само приложение Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Установка Visual Studio](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
* [Как определить параметры в файле ответов](automated-installation-with-response-file.md)
* [Управление обновлением сетевых развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
