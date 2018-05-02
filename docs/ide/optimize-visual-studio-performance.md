---
title: Повышение производительности в случае медленной работы Visual Studio
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4afd84dfaccc632143b380619a2324e607e833fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="optimize-visual-studio-performance"></a>Оптимизация производительности Visual Studio

В этой статье предлагается ряд действий, которые можно попытаться выполнить, если среда Visual Studio работает медленно. Дополнительные рекомендации по повышению производительности можно найти в статье [Советы и рекомендации по улучшению работы Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="upgrade-to-visual-studio-2017-version-156-or-later"></a>Обновление до Visual Studio 2017 версии 15.6 или более поздней

Если в настоящее время вы используете Visual Studio 2015, скачайте [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) бесплатно, чтобы ознакомиться с улучшенными возможностями этой версии. В Visual Studio 2017 решения загружаются в два-три раза быстрее. Помимо этого, оптимизирована производительность и в других областях. Версия Visual Studio 2017 совместима с Visual Studio 2015, поэтому вы не потеряете ничего при пробном использовании.

Если в настоящее время вы используете Visual Studio 2017, убедитесь в том, что у вас установлена версия 15.6 или более поздняя. По данным тестирования, в версии 15.6 решения загружаются в два–три раза быстрее. Скачать эту версию можно [здесь](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).

## <a name="extensions-and-tool-windows"></a>Расширения и окна инструментов

У вас могут быть установлены расширения, замедляющие работу Visual Studio. Сведения об управлении расширениями с целью повышения производительности см. в разделе [Изменение параметров расширений для повышения производительности](../ide/optimize-visual-studio-startup-time.md#extensions).

У вас также могут иметься окна инструментов, замедляющие работу Visual Studio. Сведения об управлении окнами инструментов см. в разделе [Изменение параметров окна инструментов для повышения производительности](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Оборудование

Если вы планируете обновление оборудования, имейте в виду, что твердотельный накопитель (SSD) сильнее влияет на производительность, чем дополнительный объем ОЗУ или ЦП с более высоким быстродействием.

Если вы добавляете диск SSD, то чтобы добиться оптимальной производительности, систему Windows следует установить на нем, а не на жестком диске (HDD). То, на каком диске находятся решения Visual Studio, не так важно.

Кроме того, не запускайте решение с USB-накопителя. Скопируйте его на жесткий диск или диск SSD.

## <a name="help-us-improve"></a>Помогите нам улучшить службу

Ваши отзывы помогают нам улучшить качество наших продуктов. Используйте функцию **Сообщить о проблеме** чтобы записать данные трассировки и отправить их нам. Щелкните значок отзыва рядом с кнопкой **быстрого запуска** или выберите в строке меню **Справка** > **Отправить отзыв** > **Сообщить о проблеме**. Дополнительные сведения см. в статье [Как сообщить о проблеме с Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>См. также

- [Советы и рекомендации по производительности](../ide/visual-studio-performance-tips-and-tricks.md)
- [Блог Visual Studio. Ускорение загрузки решений в Visual Studio 2017 версии 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)