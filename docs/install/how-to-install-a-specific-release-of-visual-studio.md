---
title: "Практическое руководство. Установка конкретного выпуска Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "установка конкретного выпуска, Visual Studio"
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
caps.handback.revision: 11
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Практическое руководство. Установка конкретного выпуска Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Программа установки Visual Studio часто обновляется, поэтому у вас всегда будет самая актуальная, оптимизированная версия дополнительных функций.  Но, если вы хотите установить более раннюю версию Visual Studio 2015, например выпуск Visual Studio без обновления 1 с поддержкой iOS, при установке Visual Studio необходимо принудительно использовать более раннюю версию файлов манифеста компонентов. В этой статье описывается, как это сделать.  
  
## Установка текущего выпуска  
 С момента первоначального выпуска Visual Studio 2015 механизм установки был обновлен один раз, а файлы манифеста — более пяти раз.  Это означает, что если [скачать и запустить программу установки Visual Studio сейчас](https://www.visualstudio.com/downloads/download-visual-studio-vs) на чистом компьютере, подключенном к Интернету, то будет установлена версия Visual Studio 2015 с обновлением 1, которая содержит последние улучшения продукта, а также новые, последние версии дополнительных компонентов и средств.  
  
## Установка более ранних выпусков  
 Можно создать и подключить ISO\-образ или загрузить и запустить непосредственно веб\-установщик, а затем добавить в EXE\-файл дополнительные параметры командной строки \(например, \/CustomInstallPath, \/Full, \/InstallSelectableItems, \/NoRestart и т. д.\) для управления способом установки Visual Studio.  
  
 В следующей таблице приведены некоторые сценарии на момент времени и необходимые параметры командной строки, которые должны быть переданы в веб\-установщик выпуска Enterprise. \(Те же параметры также будут работать с выпусками Community или Professional.\)  
  
|Выпуск Visual Studio 2015|Что запускать|Использование командной строки|Что делает программа установки|  
|-------------------------------|-------------------|------------------------------------|------------------------------------|  
|Visual Studio Enterprise \(последний общедоступный выпуск\)|Visual Studio Enterprise с обновлением 1 \(доступно на сайте [VisualStudio.com](https://www.visualstudio.com/en-us/products/vs-2015-product-editions.aspx)\)|`vs_enterprise.exe` **Note:**  По умолчанию при установке предлагаются самые последние дополнительные функции, поэтому параметры командной строки не требуются.|Программа установки Visual Studio будет использовать последнюю версию файла feed.xml и установит последние файлы|  
|Visual Studio Enterprise \(исходный RTM, но с обновлениями, вышедшими до появления обновления 1\)|Visual Studio Enterprise RTM \(доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была текущей до выпуска обновления 1|  
|Обновление 1 для Visual Studio Enterprise \(исходное обновление 1 без последующих обновлений\)|Visual Studio Enterprise с обновлением 1 \(доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Программа установки Visual Studio будет использовать версию файла feed.xml, которая была доступна в обновлении 1|  
|Visual Studio Enterprise \(исходный RTM без обновлений\)|Visual Studio Enterprise RTM \(доступно на [странице скачивания подписок MSDN](https://msdn.microsoft.com/en-us/subscriptions/downloads/)\)|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Установка Visual Studio будет использовать версию файла feed.xml, которая была доступна в RTM|  
  
> [!IMPORTANT]
>  В зависимости от языка, который вы хотите использовать, необходимо заменить "enu" \(для английского языка\) одним из следующих значений.  
>   
>  -   chs \(для китайского языка \[упрощенное письмо\]\)  
> -   cht \(для китайского языка \[традиционное письмо\]\)  
> -   csy \(для чешского языка\)  
> -   deu \(для немецкого языка\)  
> -   esn \(для испанского языка\)  
> -   fra \(для французского языка\)  
> -   ita \(для итальянского языка\)  
> -   jpa \(для японского языка\)  
> -   kor \(для корейского языка\)  
> -   plk \(для польского языка\)  
> -   ptb \(для португальского языка\)  
> -   rus \(для русского языка\)  
> -   trk \(для турецкого языка\)  
  
## См. также  
 [Установка Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)