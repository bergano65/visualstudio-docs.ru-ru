---
title: Руководство администратора Visual Studio
description: Дополнительные сведения о способах развертывания Visual Studio в корпоративной среде.
ms.custom: ''
ms.date: 05/29/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59424cdb93d8c664740ddf1d9865ba41044eb72e
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283081"
---
# <a name="visual-studio-2017-administrator-guide"></a>Руководство администратора Visual Studio 2017

В корпоративных средах системные администраторы часто развертывают установки для конечных пользователей из общего сетевого ресурса или с помощью программного обеспечения для управления системой. Мы создали механизм установки Visual Studio, который поддерживает корпоративные сценарии развертывания. Это позволяет системным администраторам создать сетевое расположение и настроить параметры по умолчанию для развертывания ключей продукта во время установки и для управления обновлениями продуктов после успешного развертывания. В этом руководстве администратора представлено руководство на основе сценария для корпоративного развертывания в сетевых окружениях.

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>Развертывание Visual Studio 2017 в корпоративной среде

Вы можете развернуть Visual Studio 2017 на клиентских компьютерах, если каждый из этих компьютеров отвечает [минимальным требованиям к установке](/visualstudio/productinfo/vs2017-system-requirements-vs). Независимо от выбранного способа развертывания (с помощью такого программного обеспечения, как System Center, или пакетного файла), как правило, выполняются следующие действия:

1. [Создайте сетевую папку, содержащую файлы продукта Visual Studio](create-a-network-installation-of-visual-studio.md) в сетевом расположении.

2. [Выбор рабочих нагрузок и компонентов](workload-and-component-ids.md), которые требуется установить.

3. [Создайте файл ответов](automated-installation-with-response-file.md) с параметрами установки по умолчанию. Также вы можете [создать сценарий установки](use-command-line-parameters-to-install-visual-studio.md), который использует параметры командной строки для управления установкой.

4. При необходимости [применение ключа корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md) в рамках скрипта установки, чтобы освободить пользователей от необходимости отдельной активации программного обеспечения.

5. Обновите сетевой макет для [управления передачей обновлений конечным пользователям](controlling-updates-to-visual-studio-deployments.md).

6. При необходимости задайте разделы реестра, [которые управляют использованием кэша на клиентских рабочих станциях](set-defaults-for-enterprise-deployments.md).

7. Выполнение созданного ранее скрипта на целевых рабочих станциях разработчиков с использованием выбранной технологии развертывания.

8. Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

> [!IMPORTANT]
> Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2017 в вашей организации.

## <a name="use-visual-studio-tools"></a>Инструменты Visual Studio

Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio](tools-for-managing-visual-studio-instances.md) на клиентских компьютерах и управления ими.

> [!TIP]
> В дополнение к документации в руководстве администратора, хорошим источником информации по установке Visual Studio 2017 будет [блог Хита Стюарта (Heath Stewart)](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="specify-customer-feedback-settings"></a>Определение настроек отзыва пользователя

По умолчанию установка Visual Studio позволяет клиентам оставлять отзывы. При включении групповой политики в Visual Studio можно настроить отключение отправки отзывов пользователей с отдельных компьютеров. Для этого задайте политику на основе реестра в следующем разделе:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Value = (DWORD)
* **0** — отказ
* **1** — согласие

Дополнительные сведения о параметрах отзывов пользователей см. на странице [Программа улучшения качества программного обеспечения Visual Studio](../ide/visual-studio-experience-improvement-program.md).

## <a name="get-support"></a>Техническая поддержка

Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:

* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем и искать решения в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/).
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio). (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Установка Visual Studio 2017](install-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
  * [Сведения об идентификаторах рабочих нагрузок и компонентов](workload-and-component-ids.md)
* [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](install-certificates-for-visual-studio-offline.md)
* [Автоматизация установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md)
* [Автоматическое применение ключей продуктов при развертывании Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Настройка параметров по умолчанию для корпоративного развертывания Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Отключение или перемещение кэша пакетов](disable-or-move-the-package-cache.md)
* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Управление обновлением развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
