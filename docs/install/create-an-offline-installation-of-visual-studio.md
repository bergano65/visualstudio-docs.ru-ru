---
title: "Создание автономной установки Visual Studio | Документы Майкрософт"
description: "Узнайте, как установить Visual Studio в автономном режиме."
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8b0902c7e2d3c2b51ecd915647a3e8a03e49c641
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2017
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Создание автономной установки Visual Studio 2017

Мы разработали установщик Visual Studio 2017 так, что он прекрасно работает с разными параметрами сетевой среды и компьютера.

- Новая модель на основе рабочих нагрузок позволяет вам скачивать меньше файлов, чем для предыдущих версий Visual Studio: всего 300 МБ для самой маленькой установки.
- Вместо универсальных файлов ISO или ZIP вы скачиваете только те пакеты, которые требуются на вашем компьютере. Например, вы не скачиваете 64-разрядные файлы, если они не нужны.
- Во время установки мы используем три разные технологии скачивания (WebClient, BITS и WinInet), чтобы меньше зависеть от работы антивирусных программ и прокси-серверов.
- Файлы, которые потребуются для установки Visual Studio, распространяются через глобальную сеть доставки, и мы можем передать их с локального сервера.

Мы рекомендуем вам опробовать [веб-установщик Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)&mdash;. Уверены, что вам понравится работать с ним.

 > [!div class="button"]
 > [Скачивание Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Если вы хотите выполнить автономную установку, так как подключение к Интернету недоступно или ненадежно, см. статью [Установка Visual Studio 2017 в сетевых средах с низкой пропускной способностью или низким уровнем надежности](../install/install-vs-inconsistent-quality-network.md). Вы можете создать локальный кэш файлов, необходимых для автономной установки, с помощью командной строки. При этом заменяются ISO-файлы, доступные для предыдущих версий.

> [!NOTE]
> Если вы являетесь администратором предприятия, которому требуется развернуть Visual Studio 2017 в сети клиентских рабочих станций, которые отделены от Интернета брандмауэром, см. статьи [Создание сетевой установки Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) и [Особые рекомендации по установке Visual Studio в автономной среде](../install/install-visual-studio-in-offline-environment.md).

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio ознакомьтесь с советами, приведенными на странице [Устранение неполадок и исправление ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Кроме того, вы можете сообщить о проблемах при использовании продукта в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md) в Visual Studio IDE или платформу [UserVoice](https://visualstudio.uservoice.com/forums/121579). Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы. Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio) (требуется учетная запись [GitHub](https://github.com/)).
