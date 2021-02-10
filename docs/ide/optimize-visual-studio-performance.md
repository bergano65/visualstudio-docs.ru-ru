---
title: Повышение производительности в случае медленной работы Visual Studio
titleSuffix: ''
description: Сведения о том, как улучшить производительность Visual Studio, если вас не устраивает скорость работы среды.
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: e1c1be9ef034f4c11fde22e8aa811785631321f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909125"
---
# <a name="optimize-visual-studio-performance"></a>Оптимизация производительности Visual Studio

В этой статье предлагается ряд действий, которые можно попытаться выполнить, если среда Visual Studio работает медленно. Дополнительные рекомендации по повышению производительности можно найти в статье [Советы и рекомендации по улучшению работы Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="upgrade-visual-studio"></a>Обновление Visual Studio

Если в настоящее время вы используете Visual Studio 2015, скачайте [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) или [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) бесплатно, чтобы ознакомиться с улучшенными возможностями этой версии. Решения загружаются в два-три раза быстрее, чем в Visual Studio 2015. Помимо этого, оптимизирована производительность и в других областях. Visual Studio 2017 и Visual Studio 2019 совместимы с Visual Studio 2015, поэтому вы не потеряете ничего при пробном использовании.

::: moniker range="vs-2017"

Если вы уже используете Visual Studio 2017, убедитесь в том, что у вас установлена версия 15.6 или более поздняя. По данным тестирования, в версии 15.6 решения загружаются в два–три раза быстрее. Его можно скачать [здесь](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Расширения и окна инструментов

У вас могут быть установлены расширения, замедляющие работу Visual Studio. Сведения об управлении расширениями с целью повышения производительности см. в разделе [Изменение параметров расширений для повышения производительности](../ide/optimize-visual-studio-startup-time.md#extensions).

У вас также могут иметься окна инструментов, замедляющие работу Visual Studio. Сведения об управлении окнами инструментов см. в разделе [Изменение параметров окна инструментов для повышения производительности](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Оборудование

Если вы планируете обновление оборудования, имейте в виду, что твердотельный накопитель (SSD) сильнее влияет на производительность, чем дополнительный объем ОЗУ или ЦП с более высоким быстродействием.

Если вы добавляете диск SSD, то чтобы добиться оптимальной производительности, систему Windows следует установить на нем, а не на жестком диске (HDD). То, на каком диске находятся решения Visual Studio, не так важно.

Кроме того, не запускайте решение с USB-накопителя. Скопируйте его на жесткий диск или диск SSD.

## <a name="help-us-improve"></a>Помогите нам улучшить службу

Ваши отзывы помогают нам улучшить качество наших продуктов. Используйте функцию **Сообщить о проблеме** чтобы записать данные трассировки и отправить их нам. Щелкните значок отзыва рядом с кнопкой **быстрого запуска** или выберите в строке меню **Справка** > **Отправить отзыв** > **Сообщить о проблеме**. Дополнительные сведения см. в статье [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>См. также раздел

- [Советы и рекомендации по производительности](../ide/visual-studio-performance-tips-and-tricks.md)
- [Блог Visual Studio. Ускорение загрузки решений в Visual Studio 2017 версии 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
