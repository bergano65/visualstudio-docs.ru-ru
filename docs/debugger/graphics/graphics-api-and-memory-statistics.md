---
title: Графический API и статистика памяти | Документация Майкрософт
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735577"
---
# <a name="graphics-api-and-memory-statistics"></a>Графический API и статистика памяти
<!-- VERSIONLESS -->
Visual Studio 2017 и более поздней версии поддерживают статистику API графики и средства статистики памяти.  Эти два средства позволяют просматривать различные биты информации об использовании Direct3D API, а также о потреблении памяти GPU различными ресурсами.

## <a name="graphics-api-statistics"></a>Статистика графического API
Статистика API графики в Visual Studio диагностика графики позволяет просматривать все выполненные вызовы Direct3D и число каждого вызова.  Чтобы открыть окно, выберите пункт меню **Просмотр статистики > API** .

![Статистика API](media/gfx_diag_api_statistics.png)

Это средство может оказаться полезным при обнаружении вызовов DirectX, которые вы не знаете, или вызывает слишком частое выполнение.

Можно щелкнуть правой кнопкой мыши в окне, чтобы скопировать все данные в CSV-файл, который можно будет вставлять в Excel для дальнейшего анализа.

## <a name="memory-statistics"></a>Статистика памяти
Это средство отображает объем памяти, выделенный драйвером графической подсистемы для ресурсов, создаваемых в кадре.  Чтобы открыть это окно, выберите пункт меню **просмотр > статистики памяти** .

![Статистика памяти](media/gfx_diag_memory_statistics.png)

В столбце **выделение GPU** отображается объем памяти, используемый событием, отображаемым в столбце **событие** .  Можно также щелкнуть значок контрольного значения ![watch значок ](media/gfx_watch.png), чтобы просмотреть [Журнал ресурсов](graphics-event-list.md#resource-history) для выбранного события.

Как и в случае со средством статистики API, можно щелкнуть правой кнопкой мыши в окне, чтобы скопировать все данные в CSV-файл, который можно будет вставлять в Excel для дальнейшего анализа.

## <a name="see-also"></a>См. также
- [Диагностика графики (отладка графики DirectX)](visual-studio-graphics-diagnostics.md)
- [Журнал ресурсов](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->