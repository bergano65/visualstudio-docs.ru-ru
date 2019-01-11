---
title: Как выполнить Установка конкретного выпуска | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 42776c20cd6634903344569f9ce1f35a776c5f86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959924"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Как выполнить Установка конкретного выпуска Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Программа установки Visual Studio часто обновляется, поэтому у вас всегда будет самая актуальная, оптимизированная версия дополнительных функций.  Но, если вы хотите установить более раннюю версию Visual Studio 2015, например выпуск Visual Studio без обновления 1 с поддержкой iOS, при установке Visual Studio необходимо принудительно использовать более раннюю версию файлов манифеста компонентов. В этой статье описывается, как это сделать.

## <a name="installing-the-current-release"></a>Установка текущего выпуска
 С момента первоначального выпуска Visual Studio 2015 мы обновили механизм установки, а также файлы манифеста несколько раз.  Это означает, что при загрузке веб-установщик [загрузки Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) веб-сайта на компьютере чистой, подключенной к Интернету, программа установки устанавливает последнюю Visual Studio 2015 обновления, включающий последние улучшения продукта а также новые, последние версии дополнительных компонентов и средств.

## <a name="installing-earlier-releases"></a>Установка более ранних выпусков
 Вы можете создать и подключить ISO-образ, или можно загрузить и запустить программу установки непосредственно из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) и добавьте в файл .exe Дополнительные параметры командной строки (например, / custominstallpath, / Full, / InstallSelectableItems, / norestart и т. д.) для управления, как устанавливается Visual Studio.

 В следующей таблице содержатся некоторые сценарии в определенный момент времени и необходимые параметры командной строки, которые должны быть переданы в установщик выпуска Enterprise. (Те же параметры также будут работать с выпусками Community или Professional.)

|Выпуск Visual Studio 2015|Что запускать|Использование командной строки|Что делает программа установки|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (последний общедоступный выпуск)|Visual Studio Enterprise с обновлениями (доступные из [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Примечание:**  По умолчанию при установке предлагаются самые последние дополнительные возможности, поэтому параметры командной строки не требуются.|Программа установки Visual Studio будет использовать последнюю версию файла feed.xml и установит последние файлы|
|Обновление 3 для Visual Studio Enterprise (исходное обновление 3 без последующих обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступна после выпуска с обновлением 3|
|Visual Studio Enterprise с обновлением 2 (исходное обновление 2, но с обновлениями, до появления обновления 3)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 3|
|Visual Studio Enterprise (исходное обновление 2 без дальнейших обновлений 2 эры обновления)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступна после выпуска с обновлением 2|
|Visual Studio Enterprise с обновлением 1 (исходное обновление 1, но с обновлениями, до появления обновления 2)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 2|
|Обновление 1 для Visual Studio Enterprise (исходное обновление 1 без последующих обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступна после выпуска с обновлением 1|
|Visual Studio Enterprise (исходный RTM, но с обновлениями, вышедшими до появления обновления 1)|Visual Studio Enterprise RTM (доступно на  [странице скачивания подписок MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 1|
|Visual Studio Enterprise (исходный RTM без обновлений)|Visual Studio Enterprise RTM (доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступна после выпуска RTM|

> [!IMPORTANT]
>  В зависимости от языка, который вы хотите использовать, необходимо заменить "enu" (для английского языка) одним из следующих значений.
>
> - chs (для китайского языка [упрощенное письмо])
>   -   cht (для китайского языка [традиционное письмо])
>   -   csy (для чешского языка)
>   -   deu (для немецкого языка)
>   -   esn (для испанского языка)
>   -   fra (для французского языка)
>   -   ita (для итальянского языка)
>   -   jpa (для японского языка)
>   -   kor (для корейского языка)
>   -   plk (для польского языка)
>   -   ptb (для португальского языка)
>   -   rus (для русского языка)
>   -   trk (для турецкого языка)

## <a name="see-also"></a>См. также раздел
 [Руководство администратора Visual Studio](../install/visual-studio-administrator-guide.md)