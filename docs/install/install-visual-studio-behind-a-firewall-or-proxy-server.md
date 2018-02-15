---
title: "Установка Visual Studio в среде, защищенной брандмауэром или прокси-сервером | Документация Майкрософт"
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
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
ms.workload: multiple
ms.openlocfilehash: 3862c6ed49e00ffa3800cccbedb2b846823418ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Установка Visual Studio в среде, защищенной брандмауэром или прокси-сервером

Установщик Visual Studio скачивает файлы с различных доменов и серверов загрузки. На этой странице перечислены URL-адреса (домены), которые может потребоваться добавить в список разрешенных (надежных) в скриптах развертывания.

Если это возможно в вашей среде, добавьте следующие домены как для протокола HTTP, так и для протокола HTTPS.

## <a name="microsoft-domains"></a>Домены Майкрософт
| Домен | Цель |
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

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также
* [Установка Visual Studio 2017](install-visual-studio.md)
* [Использование параметров командной строки для установки Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
  * [Сведения об идентификаторах рабочих нагрузок и компонентов](workload-and-component-ids.md)
* [Создание сетевой установки Visual Studio 2017](create-a-network-installation-of-visual-studio.md)
  * [Установка сертификатов, необходимых для установки Visual Studio в автономном режиме](install-certificates-for-visual-studio-offline.md)
* [Автоматизация установки Visual Studio с помощью файла ответов](automated-installation-with-response-file.md)
* [Автоматическое применение ключей продуктов при развертывании Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Настройка параметров по умолчанию для корпоративного развертывания Visual Studio 2017](set-defaults-for-enterprise-deployments.md)
* [Отключение или перемещение кэша пакетов](disable-or-move-the-package-cache.md)
* [Обновление сетевой установки Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Управление обновлением развертываний Visual Studio 2017](controlling-updates-to-visual-studio-deployments.md)
* [Средства для обнаружения экземпляров Visual Studio и управления ими](tools-for-managing-visual-studio-instances.md)
