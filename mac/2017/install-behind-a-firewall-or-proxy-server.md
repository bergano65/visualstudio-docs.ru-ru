---
title: Установка и использование Visual Studio для Mac в среде, защищенной брандмауэром или прокси-сервером
description: Этот документ содержит список узлов, которые должны быть разрешены в брандмауэре, чтобы Visual Studio для Mac (и соответствующие рабочие нагрузки, включая Xamarin) работали в корпоративной среде.
ms.topic: troubleshooting
ms.assetid: 79C0F1A3-0C13-4E55-A820-1138A4082B77
author: heiligerdankgesang
ms.author: dominicn
ms.date: 10/23/2018
ms.openlocfilehash: 738c5277ca6a669a834635f5c626e0cbabd7a7ef
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984937"
---
# <a name="install-and-use-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Установка и использование Visual Studio для Mac в среде, защищенной брандмауэром или прокси-сервером

Если вы или ваша организация используете средства обеспечения безопасности, например брандмауэр или прокси-сервер, значит есть домены, которые нужно добавить в список разрешений, а также порты и протоколы, которые нужно открыть, чтобы обеспечить оптимальную установку и использование Visual Studio для Mac и служб Azure.

- [**Установка Visual Studio для Mac**](#install-visual-studio-for-mac). Эти таблицы содержат данные о доменах, для которых нужно разрешить подключения, чтобы вы могли получить доступ ко всем функциям и рабочим нагрузкам Visual Studio для Mac.

- [**Использование Visual Studio для Mac**](#use-visual-studio-for-mac). Эти таблицы содержат данные о доменах, для которых нужно разрешить подключения, чтобы вы могли получить доступ к соответствующим функциям.

## <a name="install-visual-studio-for-mac"></a>Установка Visual Studio для Mac

Так как установщик Visual Studio для Mac загружается из различных доменов и с различных серверов загрузки, ниже приведены домены и URL-адреса, которые потребуется добавить в конфигурации в качестве доверенных.

### <a name="microsoft-domains"></a>Домены Майкрософт

| Домен| Цель |
| ----------------------------------- |---------------------------|
| *.live.com| Управление учетными данными |
| app.vssps.visualstudio.com| Метаданные установщика|
| vortex.data.microsoft.com | Отчеты о сбоях и ошибках |
| az667904.vo.msecnd.net| Отчеты о сбоях и ошибках |
| xamarin.com | Метаданные установщика|
| xampubdl.blob.core.windows.net| Пакеты установщика|
| download.visualstudio.microsoft.com | Пакеты установщика|
| xamarin.azureedge.net | Пакеты установщика|
| developer.xamarin.com | Пакеты установщика|
| dc.services.visualstudio.com| Отчеты о сбоях |

### <a name="third-party-domains"></a>Сторонние домены

| Домен| Цель |
| --------------------------|-------------------------|
| dl.google.com | Android SDK |
| download.oracle.com | Пакет SDK для Java|
| api.apple-cloudkit.com| Службы безопасности Apple |

## <a name="use-visual-studio-for-mac"></a>Использование Visual Studio для Mac

Чтобы обеспечить доступность всех функций, которые могут потребоваться в Visual Studio для Mac во время работы в среде, защищенной прокси-сервером или брандмауэром, мы рекомендуем добавить следующие домены и порты в список разрешений.

### <a name="general"></a>Общее

| Домен | Порты|Цель|
| ----------------------|------------------|------------------|
| go.microsoft.com | 80/443|Разрешение URL-адресов Майкрософт |
| vsstartpage.blob.core.windows.net| 80/443| Данные начальной страницы|
| software.xamarin.com |  80/443|Служба обновления|
| addins.monodevelop.com | 80/443| Службы расширения |
| visualstudio-devdiv-c2s.msedge.net | 80/443| Экспериментальные функции и уведомления |
| targetednotifications.azurewebsites.net|  80/443| Используется для фильтрации глобального списка уведомлений, чтобы сделать его применимым только к определенным типам компьютеров и сценариев использования|

### <a name="identity"></a>идентификации

| Домен | Порты|Цель|
| ----------------------|------------------|------------------|
| login.microsoftonline.com | 80/443| Поставщик удостоверений|
| secure.aadcdn.microsoftonline-p.com | 80/443|Поставщик удостоверений|
| dc.services.visualstudio.com| 80/443|Отчеты о сбоях|
| management.azure.com|80/443| API служб Azure |

### <a name="nuget"></a>NuGet

| Домен | Порты|Цель|
| ----------------------|------------------|------------------|
| api.nuget.org | 80/443|API NuGet|
| secure.aadcdn.microsoftonline-p.com |80/443| Поставщик удостоверений|

### <a name="android-projects"></a>Проекты Android

| Домен| Цель|
| ------------------------------------|------------------------------------|
| time.android.com| Сервер времени для Android Emulator |
| connectivitycheck.gstatic.com | Подключение для Android Emulator|
| cloudconfig.googleapis.com| API-интерфейсы для Android Emulator|

## <a name="see-also"></a>См. также

- [Установка и использование Visual Studio 2017 и служб Azure, расположенных за брандмауэром или прокси-сервером](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server)
- [Исправление схожих ошибок в Windows](/visualstudio/install/troubleshooting-network-related-errors-in-visual-studio)
