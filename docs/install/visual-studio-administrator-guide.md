---
title: "Руководство администратора Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 04/06/2017
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
translationtype: Human Translation
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: aebd3abc671f997773fc7c557627ca23b9bf82bd
ms.lasthandoff: 04/06/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Руководство администратора Visual Studio 2017

 Visual Studio можно развертывать в сети, если каждый конечный компьютер отвечает [минимальным требованиям для установки](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 Независимо от выбранного способа развертывания (с помощью такого программного обеспечения, как System Center, или пакетного файла), как правило, выполняются следующие действия:

1. [Создание кэша структуры продукта Visual Studio](create-an-offline-installation-of-visual-studio.md) в сетевой папке.

2. [Выбор рабочих нагрузок и компонентов](workload-and-component-ids.md), которые требуется установить.

3. [Сборка скрипта установки](use-command-line-parameters-to-install-visual-studio.md) с использованием выбранных элементов и других параметров командной строки, определяющих свойства установки.

4. При необходимости [применение ключа корпоративной лицензии](automatically-apply-product-keys-when-deploying-visual-studio.md) в рамках скрипта установки, чтобы освободить пользователей от необходимости отдельной активации программного обеспечения.

5. Выполнение созданного ранее скрипта на целевых рабочих станциях разработчиков с использованием выбранной технологии развертывания.

6. Регулярная установка последних обновлений Visual Studio в расположениях в сети с помощью команды, используемой на шаге 1, для добавления новых компонентов.

> [!IMPORTANT]
>  Обратите внимание, что установки из общей сетевой папки "запоминают" исходное расположение, из которого они выполнялись. Это означает, что при восстановлении клиентского компьютера может потребоваться вернуться к сетевой папке, из которой клиент был установлен изначально. В связи с этим необходимо внимательно отнестись к выбору сетевых расположений, которые должны соответствовать времени существования клиентов Visual Studio 2017 в вашей организации.

## <a name="tools"></a>Инструменты

 Мы предлагаем несколько средств, предназначенных для обнаружения установленных экземпляров Visual Studio на клиентских компьютерах и управления ими:

* [VSWhere](https://github.com/microsoft/vswhere). Исполняемый файл C++, с помощью которого можно определить местоположение базовых инструментов Visual Studio для установленного экземпляра Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell). Скрипты PowerShell, которые позволяют определить установленные экземпляры Visual Studio с помощью API конфигурации установки.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples). Образцы на языках C# и C++, демонстрирующие применение API конфигурации установки для запроса существующей установки.

Кроме того, [API конфигурации установки](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) реализует интерфейсы для разработчиков, которые хотят создавать свои собственные служебные программы для опроса экземпляров Visual Studio.

>[!TIP]
>Дополнительные сведения об установке Visual Studio 2017 г. в [статьях блога Хита Стюарта (Heath Stewart)](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Создание автономного установщика Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Сообщение о проблеме с помощью Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

