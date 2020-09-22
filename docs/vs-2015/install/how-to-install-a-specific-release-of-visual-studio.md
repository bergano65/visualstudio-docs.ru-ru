---
title: Практическое руководство. Установка определенного выпуска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842924"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Практическое руководство. Установка конкретного выпуска Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Программа установки Visual Studio часто обновляется, поэтому у вас всегда будет самая актуальная, оптимизированная версия дополнительных функций.  Но, если вы хотите установить более раннюю версию Visual Studio 2015, например выпуск Visual Studio без обновления 1 с поддержкой iOS, при установке Visual Studio необходимо принудительно использовать более раннюю версию файлов манифеста компонентов. В этой статье описывается, как это сделать.

## <a name="installing-the-current-release"></a>Установка текущего выпуска
 С момента первоначального выпуска Visual Studio 2015 механизм установки и файлы манифеста были несколько раз обновлены.  Это означает следующее. Если вы скачаете веб-установщик с веб-сайта со [скачиваемыми файлами Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) на подготовленный компьютер, подключенный к Интернету, будет установлена последняя версия Visual Studio 2015. Она содержит последние улучшения продукта, а также последние версии дополнительных компонентов и средств.

## <a name="installing-earlier-releases"></a>Установка более ранних выпусков
 Вы можете создать и подключить ISO-образ или скачать установщик непосредственно с веб-сайта [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) и запустить его, а затем добавить в EXE-файл дополнительные параметры командной строки (например, /CustomInstallPath, /Full, /InstallSelectableItems, /NoRestart и т. д.) для управления установкой Visual Studio.

 В следующей таблице приведены некоторые сценарии на определенный момент времени и необходимые параметры командной строки, которые нужно передать веб-установщику выпуска Enterprise. (Те же параметры также будут работать с выпусками Community или Professional.)

|Выпуск Visual Studio 2015|Что запускать|Использование командной строки|Что делает программа установки|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (последний общедоступный выпуск)|Visual Studio Enterprise с обновлениями (доступно на сайте [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Примечание.** По умолчанию эта установка предлагает последние версии дополнительных компонентов, поэтому параметры командной строки для нее не требуются.|Программа установки Visual Studio будет использовать последнюю версию файла feed.xml и установит последние файлы|
|Обновление 3 для Visual Studio Enterprise (исходное обновление 3 без последующих обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступной на момент выпуска обновления 3|
|Visual Studio Enterprise с обновлением 2 (исходное обновление 2, но с обновлениями, вышедшими до выпуска обновления 3)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 3|
|Visual Studio Enterprise (исходное обновление 2 без последующих обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступной на момент выпуска обновления 2|
|Visual Studio Enterprise с обновлением 1 (исходное обновление 1, но с обновлениями, вышедшими до выпуска обновления 2)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 2|
|Обновление 1 для Visual Studio Enterprise (исходное обновление 1 без последующих обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступной на момент выпуска обновления 1|
|Visual Studio Enterprise (исходный RTM, но с обновлениями, вышедшими до появления обновления 1)|Visual Studio Enterprise RTM (доступна на  [странице загрузки подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 1|
|Visual Studio Enterprise (исходный RTM без обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступной на момент выпуска RTM|

> [!IMPORTANT]
> В зависимости от языка, который вы хотите использовать, необходимо заменить "enu" (для английского языка) одним из следующих значений.
>
> - chs (для китайского языка [упрощенное письмо])
>   - cht (для китайского языка [традиционное письмо])
>   - csy (для чешского языка)
>   - deu (для немецкого языка)
>   - esn (для испанского языка)
>   - fra (для французского языка)
>   - ita (для итальянского языка)
>   - jpa (для японского языка)
>   - kor (для корейского языка)
>   - plk (для польского языка)
>   - ptb (для португальского языка)
>   - rus (для русского языка)
>   - trk (для турецкого языка)

## <a name="see-also"></a>См. также:
 [Руководством администратора Visual Studio](../install/visual-studio-administrator-guide.md)