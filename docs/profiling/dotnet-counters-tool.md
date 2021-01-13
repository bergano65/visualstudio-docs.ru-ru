---
title: Визуализация счетчиков dotnet | Документация Майкрософт
description: Узнайте, как использовать средство "Счетчики .NET" в Профилировщике производительности Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905076"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Визуализация счетчиков dotnet из профилировщика Visual Studio


Средство "Счетчики .NET" позволяет визуализировать [счетчики dotnet](/dotnet/core/diagnostics/dotnet-counters) с течением времени с помощью профилировщика Visual Studio.


> [!NOTE]
> Для работы средства "Счетчики .NET" требуется Visual Studio 2019 версии 16.7 или более поздней и целевой платформы .NET Core 3.0 или более поздней версии.

## <a name="setup"></a>Настройка

1. Откройте Профилировщик производительности (**Alt + F2** или **Отладка > Профилировщик производительности**) в Visual Studio.

2. Установите флажок **Счетчики .NET**.

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Экран &quot;Окно с выбранным пунктом &quot;Счетчики .NET&quot;.":::

3. Нажмите кнопку **Запуск**, чтобы запустить средство.

Дополнительные сведения о том, как оптимизировать производительность инструментов, см. в статье [Оптимизация параметров Профилировщика](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Анализ данных

Пока средство изначально собирает данные, вы можете увидеть динамические значения [счетчиков dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Экран &quot;Сбор данных Счетчиком .NET.&quot;":::

Графики счетчиков можно также просмотреть, установив флажок рядом с именами счетчиков. Вы можете одновременно отобразить графики для нескольких счетчиков.


Завершив работу с приложением и окончив сбор данных, сбор данных можно приостановить. При этом вы получите даже еще более подробный отчет. Для этого нажмите кнопку **Остановить сбор**.


Когда отчет загрузится, вы должны увидеть окончательный отчет, аналогичный показанному ниже.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Экран &quot;Отчет средства &quot;Счетчик .NET&quot;.":::

В отчете отображаются следующие значения:

- Min — минимальное значение для этого счетчика в выбранном диапазоне.
- Max — максимальное значение для этого счетчика в выбранном диапазоне.
- Average — среднее значение для этого счетчика в выбранном диапазоне.

Столбцы в таблице можно фильтровать или добавлять, щелкнув правой кнопкой мыши заголовки столбцов и выбрав заголовок.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Экран &quot;Столбцы средства &quot;Счетчик .NET&quot;.":::

Вы можете также просматривать графики в подробном отчете, установив флажки рядом со счетчиками. Данные в таблицах по умолчанию представляют собой значения всей продолжительности сбора данных трассировки. Чтобы отфильтровать данные по определенному диапазону времени, щелкните и перетащите график.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Экран &quot;Фильтрация за временем в средстве &quot;Счетчики .NET&quot;.":::

Таблица обновляется и отображает соответствующие значения для времени, выбранного на графике. Используйте кнопку **Очистить выделение**, чтобы отменить выбор диапазона времени для всей трассировки.


## <a name="see-also"></a>См. также

- [Оптимизация параметров профилировщика](../profiling/optimize-profiler-settings.md)
- [счетчики dotnet](/dotnet/core/diagnostics/dotnet-counters)
