---
title: "Установка Visual Studio в среде, защищенной брандмауэром или прокси-сервером | Документация Майкрософт"
description: 
ms.custom: 
ms.date: 08/01/2017
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
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 0803ea25bd8f45d79d618ff481094fb5786b1acb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/14/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Установка Visual Studio в среде, защищенной брандмауэром или прокси-сервером

Установщик Visual Studio скачивает файлы с различных доменов и серверов загрузки. На этой странице перечислены URL-адреса (домены), которые может потребоваться добавить в список разрешенных (надежных) в скриптах развертывания.

Если это возможно в вашей среде, добавьте следующие домены как для протокола HTTP, так и для протокола HTTPS.

## <a name="microsoft-domains"></a>Домены Майкрософт
| Домен | Назначение |
| ------ | ------- |
| go.microsoft.com | Настройка разрешения URL-адресов |
| aka.ms | Настройка разрешения URL-адресов |
| download.visualstudio.microsoft.com | Настройка расположения для скачивания пакетов |
| download.microsoft.com | Настройка расположения для скачивания пакетов |
| download.visualstudio.com | Настройка расположения для скачивания пакетов |
| dl.xamarin.com | Настройка расположения для скачивания пакетов |
| visualstudiogallery.msdn.microsoft.com | Расположение для скачивания расширений Visual Studio |
| www.visualstudio.com | Расположение документации |
| docs.microsoft.com | Расположение документации |
| msdn.microsoft.com | Расположение документации |
| www.microsoft.com | Расположение документации |
| *.windows.net | Расположение входа |
| *.microsoftonline.com | Расположение входа |
| *.live.com | Расположение входа |


## <a name="non-microsoft-domains"></a>Сторонние домены
| Домен | Устанавливает эти рабочие нагрузки |
| ------ | ------- |
| archive.apache.org |  Разработка мобильных приложений на языке JavaScript <br />(Cordova) |
| cocos2d-x.org | Разработка игр на C++ <br />(Cocos) |
| download.epicgames.com | Разработка игр на C++ <br />(Unreal Engine) |
| download.oracle.com | Разработка мобильных приложений на языке JavaScript <br />(пакет SDK для Java) <br /><br />Разработка мобильных приложений на платформе .NET <br />(пакет SDK для Java) |
| download.unity3d.com | Разработка игр с помощью Unity <br />(Unity) |
| netstorage.unity3d.com | Разработка игр с помощью Unity <br /> (Unity) |
| dl.google.com | Разработка мобильных приложений на языке JavaScript <br />(Пакеты SDK и NDK для Android, эмулятор) <br /><br />Разработка мобильных приложений на платформе .NET <br />(Пакеты SDK и NDK для Android, эмулятор) |
| www.incredibuild.com | Разработка игр на C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Разработка игр на C++ <br />(IncrediBuild) |
| www.python.org | Разработка на Python <br />(Python) <br /><br />Приложения для обработки и анализа данных и аналитические приложения <br />(Python) |

## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
  * [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [Примеры параметров командной строки](command-line-parameter-examples.md)
    * [Сведения об идентификаторах рабочих нагрузок и компонентов](workload-and-component-ids.md)
  * [Создание сетевой установки Visual Studio](create-a-network-installation-of-visual-studio.md)
    * [Особые рекомендации по установке Visual Studio в автономной среде](install-visual-studio-in-offline-environment.md)
  * [Автоматизация установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md)
  * [Автоматическое применение ключей продуктов при развертывании Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Настройка параметров по умолчанию для корпоративного развертывания Visual Studio](set-defaults-for-enterprise-deployments.md)
  * [Отключение или перемещение кэша пакетов](disable-or-move-the-package-cache.md)
  * [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
  * [Управление обновлением развертываний Visual Studio](controlling-updates-to-visual-studio-deployments.md)
  * [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
  * [Сообщение о проблеме с помощью Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

