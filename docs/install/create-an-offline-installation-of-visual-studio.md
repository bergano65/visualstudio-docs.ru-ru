---
title: Создание автономной установки Visual Studio | Документы Майкрософт
description: Узнайте, как установить Visual Studio в автономном режиме.
ms.custom: ''
ms.date: 01/17/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 116e1821575b1a5e4e95e43eed0f175d85e9278f
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2018
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
> Если вы являетесь администратором предприятия и вам нужно развернуть Visual Studio 2017 в сети клиентских рабочих станций, которые отделены от Интернета брандмауэром, см. руководства по [созданию сетевой установки Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) и [установке сертификатов, требуемых для автономной установки Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)
