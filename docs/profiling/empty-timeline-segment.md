---
title: Пустой сегмент временной шкалы | Документы Майкрософт
description: В визуализаторе параллелизма Visual Studio изучите причину, по которой часть временной шкалы может быть пустой (имеет белый фон) в зависимости от типа канала.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15dc4526ce101e21c00fe083b85f81db92bcd609
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801433"
---
# <a name="empty-timeline-segment"></a>Пустой сегмент временной шкалы
В визуализаторе параллелизма причина, по которой часть временной шкалы пуста (имеет белый фон), зависит от типа канала.

- Для канала потока ЦП это означает, что поток не существовал на этом промежутке временной шкалы. Если вы заинтересованы в потоке, можно найти соответствующий промежуток выполнения, используя элементы управления масштабирования или прокрутки по горизонтали.

- Для канала ввода-вывода это означает, что в данный момент времени не выполнялся доступ к диску от имени целевого процесса.

- Для канала DirectX это означает, что никакая работа графического процессора не выполнялась от имени целевого процесса в этом промежутке временной шкалы.

- Для канала маркеров это означает, что маркеры не создавались.

## <a name="see-also"></a>См. также
- [Представление потоков](../profiling/threads-view-parallel-performance.md)
- [Элемент управления масштабом (представление "Потоки")](../profiling/zoom-control-threads-view.md)