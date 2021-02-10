---
title: Руководство администратора Visual Studio
titleSuffix: ''
description: Дополнительные сведения о способах развертывания Visual Studio в корпоративной среде.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecf1dc0332a023a67f2627d852ee56a092830b7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935616"
---
# <a name="visual-studio-administrator-guide"></a>Руководство администратора Visual Studio

В корпоративных средах системные администраторы часто развертывают установки для конечных пользователей из общего сетевого ресурса или с помощью программного обеспечения для управления системой. Мы создали механизм установки Visual Studio, который поддерживает корпоративные сценарии развертывания. Это позволяет системным администраторам создать сетевое расположение и настроить параметры по умолчанию для развертывания ключей продукта во время установки и для управления обновлениями продуктов после успешного развертывания.

В этом руководстве администратора представлено руководство на основе сценария для корпоративного развертывания в сетевых окружениях.

## <a name="before-you-begin"></a>Подготовка к работе

Перед развертыванием Visual Studio в вашей организации нужно принять определенные решения и выполнить задачи:

::: moniker range="vs-2019"

* Убедитесь, что каждый конечный компьютер отвечает [минимальным требованиям к установке](/visualstudio/releases/2019/system-requirements/).

* Определите потребности обслуживания.

  Если организации требуется подольше оставаться на определенном наборе функций, но также нужно получать регулярные обновления обслуживания, следует использовать план обслуживания. Дополнительные сведения см. в разделе ***Варианты поддержки для клиентов Enterprise и Professional*** статьи [Жизненный цикл и обслуживание продукта Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers), а также в статье [Обновление Visual Studio во время обслуживания](update-servicing-baseline.md).

  Если вы планируете применять обновления вместе с накопительным пакетом обновлений, вы можете обойтись последними обновлениями.

* Выберите модель обновления.

  Нуждаются ли отдельные клиентские компьютеры в получении обновлений? В частности, решите, хотите ли вы получать обновления из Интернета или из локальной общей папки всей компании. Если вы решили использовать локальный общий ресурс, решите, могут ли отдельные пользователи обновлять свои собственные клиенты, или необходимо, чтобы администратор программным способом обновлял клиенты.

  Вы можете обновить макет сетевой установки Visual Studio, включив последнее обновление продукта, чтобы использовать его в качестве точки установки обновлений Visual Studio и обеспечить поддержку уже развернутых установок на клиентских рабочих станциях. Дополнительные сведения см. в статье [Обновление сетевой установки Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Для компьютеров, не подключенных к Интернету, создание минимального макета — самый простой и быстрый способ обновления автономных экземпляров Visual Studio. Дополнительные сведения см. в статье [Обновление Visual Studio с использованием минимального автономного макета](update-minimal-layout.md).

* Решите, какой набор [рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2019&preserve-view=true) отвечает потребностям вашей компании.

* Решите, следует ли использовать [файл ответов](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (это упрощает управление сведениями в файле скрипта).

* Решите, нужно ли включение групповой политики и хотите ли вы отключить в Visual Studio отправку отзывов пользователей с отдельных компьютеров.

::: moniker-end

::: moniker range="vs-2017"

* Убедитесь, что каждый конечный компьютер отвечает [минимальным требованиям к установке](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Определите потребности обслуживания.

  Если организации требуется подольше оставаться на определенном наборе функций, но также нужно получать регулярные обновления обслуживания, следует использовать план обслуживания. Дополнительные сведения см. в разделе ***Поддержка предыдущих версий Visual Studio*** статьи [Жизненный цикл и обслуживание продукта Visual Studio](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio), а также в статье [Обновление Visual Studio во время обслуживания](update-servicing-baseline.md).

  Если вы планируете применять обновления вместе с накопительным пакетом обновлений, вы можете обойтись последними обновлениями.

* Выберите модель обновления.

  Нуждаются ли отдельные клиентские компьютеры в получении обновлений? В частности, решите, хотите ли вы получать обновления из Интернета или из локальной общей папки всей компании. Если вы решили использовать локальный общий ресурс, решите, могут ли отдельные пользователи обновлять свои собственные клиенты, или необходимо, чтобы администратор программным способом обновлял клиенты.

  Вы можете обновить макет сетевой установки Visual Studio, включив последнее обновление продукта, чтобы использовать его в качестве точки установки обновлений Visual Studio и обеспечить поддержку уже развернутых установок на клиентских рабочих станциях. Дополнительные сведения см. в статье [Обновление сетевой установки Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Для компьютеров, не подключенных к Интернету, создание минимального макета — самый простой и быстрый способ обновления автономных экземпляров Visual Studio. Дополнительные сведения см. в статье [Обновление Visual Studio с использованием минимального автономного макета](update-minimal-layout.md).

* Решите, какой набор [рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2017&preserve-view=true) отвечает потребностям вашей компании.

* Решите, следует ли использовать [файл ответов](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (это упрощает управление сведениями в файле скрипта).

* Решите, нужно ли включение групповой политики и хотите ли вы отключить в Visual Studio отправку отзывов пользователей с отдельных компьютеров.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Шаг 1.Скачивание файлов продукта Visual Studio

* [Выберите набор рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2019&preserve-view=true), которые требуется установить.

* [Создайте общую сетевую папку для файлов продукта Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Шаг 2. Создание скрипта установки

* Создайте скрипт установки, который использует [параметры командной строки](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) для управления установкой.

  >[!NOTE]
  > Его можно упростить с помощью [файла ответов](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Обязательно создайте файл ответов с параметрами установки по умолчанию.

* Также вы можете [применить ключ корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) в рамках скрипта установки, чтобы освободить пользователей от дополнительных действия для активации программного обеспечения.

* При необходимости обновите структуру сети для [управления временем и источником обновлений для конечных пользователей](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* При необходимости можно задать политики реестра, влияющие на развертывание Visual Studio, например, место, где установлены некоторые пакеты, используемые совместно с другими версиями или экземплярами, [где кэшируются пакеты](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) или [кэшируются ли пакеты вообще](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true).

* При необходимости задайте групповую политику. Также можно настроить в Visual Studio [отключение отправки отзывов пользователей с отдельных компьютеров](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy"></a>Шаг 3. Развертывание

* Примените любую удобную технологию развертывания, чтобы выполнить скрипт на целевых рабочих станциях разработчиков.

## <a name="step-4---deploy-updates"></a>Шаг 4. Развертывание обновлений

* Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

  Visual Studio можно обновить с помощью скрипта обновления. Чтобы сделать это, используйте параметр командной строки [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-5---optional-use-visual-studio-tools"></a>Шаг 5. Использование инструментов Visual Studio

Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) на клиентских компьютерах и управления ими.

## <a name="advanced-configuration"></a>Расширенная конфигурация

По умолчанию установка Visual Studio позволяет включать в поиск Bing пользовательские типы из списка ошибок F1 и ссылок на код. Можно настроить Visual Studio таким образом, чтобы запретить включение пользовательских типов в механизм поиска. Для этого необходимо изменить значение следующего раздела реестра для политики:

**"PutCustomTypeInBingSearch" DWORD 0**

Этот раздел находится в каталоге *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* частного куста реестра. Инструкции по открытию куста реестра см. в разделе [Редактирование реестра для экземпляра Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Шаг 1.Скачивание файлов продукта Visual Studio

* [Выберите набор рабочих нагрузок и компонентов](workload-and-component-ids.md?view=vs-2017&preserve-view=true), которые требуется установить.

* [Создайте общую сетевую папку для файлов продукта Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Шаг 2. Создание скрипта установки

* Создайте скрипт установки, который использует [параметры командной строки](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) для управления установкой.

  >[!NOTE]
  > Его можно упростить с помощью [файла ответов](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Обязательно создайте файл ответов с параметрами установки по умолчанию.

* Также вы можете [применить ключ корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) в рамках скрипта установки, чтобы освободить пользователей от дополнительных действия для активации программного обеспечения.

* При необходимости обновите структуру сети для [управления временем и источником обновлений для конечных пользователей](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* При необходимости можно задать политики реестра, влияющие на развертывание Visual Studio, например, место, где установлены некоторые пакеты, используемые совместно с другими версиями или экземплярами, [где кэшируются пакеты](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) или [кэшируются ли пакеты вообще](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* При необходимости задайте групповую политику. Также можно настроить в Visual Studio [отключение отправки отзывов пользователей с отдельных компьютеров](../ide/visual-studio-experience-improvement-program.md).

## <a name="step-3---deploy"></a>Шаг 3. Развертывание

* Примените любую удобную технологию развертывания, чтобы выполнить скрипт на целевых рабочих станциях разработчиков.

## <a name="step-4---deploy-updates"></a>Шаг 4. Развертывание обновлений

* Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

  Visual Studio можно обновить с помощью скрипта обновления. Чтобы сделать это, используйте параметр командной строки [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-5---optional-use-visual-studio-tools"></a>Шаг 5. Использование инструментов Visual Studio

Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) на клиентских компьютерах и управления ими.

## <a name="advanced-configuration"></a>Расширенная конфигурация

По умолчанию установка Visual Studio позволяет включать в поиск Bing пользовательские типы из списка ошибок F1 и ссылок на код. Можно настроить Visual Studio таким образом, чтобы запретить включение пользовательских типов в механизм поиска. Для этого необходимо изменить значение следующего раздела реестра для политики:

**"PutCustomTypeInBingSearch" DWORD 0**

Этот раздел находится в каталоге *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\* частного куста реестра. Инструкции по открытию куста реестра см. в разделе [Редактирование реестра для экземпляра Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](install-certificates-for-visual-studio-offline.md)
* [Импорт или экспорт конфигураций установки](import-export-installation-configurations.md)
* [Архивы установки Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Жизненный цикл и обслуживание продуктов Visual Studio](/visualstudio/releases/2019/servicing/)
* [Параметры синхронной автозагрузки](../extensibility/synchronously-autoloaded-extensions.md)
