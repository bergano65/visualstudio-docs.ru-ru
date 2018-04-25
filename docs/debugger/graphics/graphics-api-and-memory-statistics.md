---
title: Графические API и статистику использования памяти | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48c8ed3c8c2ebffc57ac46e987dbc37950cba0fd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-api-and-memory-statistics"></a>Графические API и статистику использования памяти
<!-- VERSIONLESS -->
Visual Studio 2017 г. и расширенную поддержку статистики API графики и средства статистику использования памяти.  Эти два средства позволяют просматривать различные части сведений об использовании Direct3D API, а также потребление памяти GPU различные ресурсы.

## <a name="graphics-api-statistics"></a>Статистика API графики
Статистические показатели графики API диагностики графики Visual Studio позволяет просматривать все вызовы Direct3D, которые были сделаны и счетчик для каждого вызова.  Чтобы открыть окно, выберите **представление > Статистика API** элемента меню.

![Статистика API](media/gfx_diag_api_statistics.png)

Это средство может оказаться удобным в обнаружении, что вызовы DirectX, могут не осознавать, вы вносите или вызовов, выполняемых в слишком часто.

Можно щелкнуть правой кнопкой мыши в окне, чтобы копировать все данные как CSV, который может быть вставлено в примерно Excel для дальнейшего анализа.

## <a name="memory-statistics"></a>Статистику использования памяти
Это средство отображает объем памяти, графический драйвер является выделение ресурсов, создание в кадре.  Чтобы открыть это окно, выберите **представление > статистику использования памяти** элемента меню.

![Статистику использования памяти](media/gfx_diag_memory_statistics.png)

**Выделения GPU** столбец показывает объем памяти, использованного событием, отображаются в **событие** столбца.  Вы также можете выбрать значок ![значок просмотра](media/gfx_watch.png) для просмотра [журнал ресурсов](graphics-event-list.md#resource-history) для выбранного события.

С помощью API статистики можно щелкнуть правой кнопкой мыши в окне, чтобы копировать все данные как CSV, который может быть вставлено в примерно Excel для дальнейшего анализа.

## <a name="see-also"></a>См. также  
[Диагностика графики (Отладка графики DirectX)](visual-studio-graphics-diagnostics.md)   
[Журнал ресурсов](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->