---
title: Создание автономной установки Visual Studio
description: Узнайте, как установить Visual Studio в автономном режиме.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138881"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Создание автономной установки Visual Studio 2017

Мы разработали установщик Visual Studio 2017 так, что он прекрасно работает с разными параметрами сетевой среды и компьютера.

- Новая модель на основе рабочих нагрузок позволяет вам скачивать меньше файлов, чем для предыдущих версий Visual Studio: всего 300 МБ для самой маленькой установки.
- Вместо универсальных файлов ISO или ZIP вы скачиваете только те пакеты, которые требуются на вашем компьютере. Например, вы не скачиваете 64-разрядные файлы, если они не нужны.
- Во время установки мы используем три разные технологии скачивания (WebClient, BITS и WinInet), чтобы меньше зависеть от работы антивирусных программ и прокси-серверов.
- Файлы, которые потребуются для установки Visual Studio, распространяются через глобальную сеть доставки, и мы можем передать их с локального сервера.

Мы рекомендуем вам опробовать [веб-установщик Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;. Уверены, что вам понравится работать с ним.

 > [!div class="button"]
 > [Скачивание Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Если вы хотите выполнить автономную установку, так как подключение к Интернету недоступно или ненадежно, см. статью [Установка Visual Studio 2017 в сетевых средах с низкой пропускной способностью или низким уровнем надежности](../install/install-vs-inconsistent-quality-network.md). Вы можете создать локальный кэш файлов, необходимых для автономной установки, с помощью командной строки. При этом заменяются ISO-файлы, доступные для предыдущих версий.

> [!NOTE]
> Если вы являетесь администратором предприятия и вам нужно развернуть Visual Studio 2017 в сети клиентских рабочих станций, которые отделены от Интернета брандмауэром, см. руководства по [созданию сетевой установки Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) и [установке сертификатов, требуемых для автономной установки Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
