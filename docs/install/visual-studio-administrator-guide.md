---
title: "Руководство администратора Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 05/06/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: ru-ru
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Руководство администратора Visual Studio 2017

В корпоративных средах системные администраторы часто развертывают установки для конечных пользователей из общего сетевого ресурса или с помощью программного обеспечения для управления системой. Мы создали механизм установки Visual Studio, который поддерживает корпоративные сценарии развертывания. Это позволяет системным администраторам создать сетевое расположение и настроить параметры по умолчанию для развертывания ключей продукта во время установки и для управления обновлениями продуктов после успешного развертывания. В этом руководстве администратора представлено руководство на основе сценария для корпоративного развертывания в типичных сетевых средах.

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>Действия для развертывания Visual Studio 2017 в корпоративной среде.

Вы можете развернуть Visual Studio 2017 на клиентских компьютерах, если каждый из этих компьютеров отвечает [минимальным требованиям к установке](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Независимо от выбранного способа развертывания (с помощью такого программного обеспечения, как System Center, или пакетного файла), как правило, выполняются следующие действия:

1. [Создайте сетевую папку, содержащую файлы продукта Visual Studio](create-a-network-installation-of-visual-studio.md) в сетевом расположении.

2. [Выберите рабочие нагрузки и компоненты](workload-and-component-ids.md), которые нужно установить.

3. [Создайте файл ответов](automated-installation-with-response-file.md) с параметрами установки по умолчанию. Также вы можете [создать скрипт установки](use-command-line-parameters-to-install-visual-studio.md) с параметрами командной строки для управления установкой.

4. Также вы можете [применить ключ корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md) в рамках скрипта установки, чтобы освободить пользователей от дополнительных действия для активации программного обеспечения.

5. Обновите сетевой макет для [управления передачей обновлений конечным пользователям](controlling-updates-to-visual-studio-deployments.md).

6. При необходимости задайте разделы реестра, [которые управляют использованием кэша на клиентских рабочих станциях](set-defaults-for-enterprise-deployments.md).

7. Примените любую удобную технологию развертывания, чтобы выполнить созданный ранее скрипт на целевых рабочих станциях разработчиков.

8. Регулярно [дополняйте расположение сетевой установки последними обновлениями](update-a-network-installation-of-visual-studio.md) для Visual Studio, повторно выполняя команду из шага 1 для добавления новых компонентов.

> [!IMPORTANT]
> Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2017 в вашей организации.

## <a name="tools"></a>Инструменты
Мы предлагаем несколько средств, предназначенных для [обнаружения установленных экземпляров Visual Studio на клиентских компьютерах и управления ими](tools-for-managing-visual-studio-instances.md).

> [!TIP]
> В дополнение к документации в руководстве администратора, хорошим источником информации по установке Visual Studio 2017 будет [блог Хита Стюарта (Heath Stewart)](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Установка Visual Studio в автономных средах](install-visual-studio-in-offline-environment.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Сообщение о проблеме с помощью Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

