---
title: Граф активности GPU | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9dcadfdbfa52815fdd6d88f78afb88d421e203c7
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237914"
---
# <a name="gpu-activity-graph"></a>Граф активности GPU
Граф активности GPU в визуализаторе параллелизма отображает уровень активности DirectX в системе, измеренный по числу ядер DirectX, которые используются в динамике по времени.  Граф не показывает, какие конкретные ядра были использованы.  Ядро считается используемым, если оно выполняет какую-либо работу графического процессора.  
  
## <a name="gpu-activity-graph-colors"></a>Цвета на графе активности GPU  
 Зеленый цвет обозначает потребление ядер DirectX текущим процессом.  
  
 Светло-серый цвет обозначает потребление ядер DirectX другими процессами в системе. Чтобы уменьшить потребление ядер DirectX другими процессами, сократите число других процессов, выполняющихся в системе.  
  
 Белый цвет указывает на наличие неиспользуемых ядер DirectX в системе. Эти ядра доступны для процесса, если вам удастся найти дополнительные возможности для их использования. Некоторые ядра могут использоваться только для определенных видов задач.  
  
## <a name="see-also"></a>См. также  
 [Представление "Использование"](../profiling/utilization-view.md)