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
ms.openlocfilehash: 41b7812db05b61c351346e5f0dcfa1bf4bd7bd1f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-graph"></a>Граф активности GPU
Граф активности GPU в визуализаторе параллелизма отображает уровень активности DirectX в системе, измеренный по числу ядер DirectX, которые используются в динамике по времени.  Граф не показывает, какие конкретные ядра были использованы.  Ядро считается используемым, если оно выполняет какую-либо работу графического процессора.  
  
## <a name="gpu-activity-graph-colors"></a>Цвета на графе активности GPU  
 Зеленый цвет обозначает потребление ядер DirectX текущим процессом.  
  
 Светло-серый цвет обозначает потребление ядер DirectX другими процессами в системе. Чтобы уменьшить потребление ядер DirectX другими процессами, сократите число других процессов, выполняющихся в системе.  
  
 Белый цвет указывает на наличие неиспользуемых ядер DirectX в системе. Эти ядра доступны для процесса, если вам удастся найти дополнительные возможности для их использования. Некоторые ядра могут использоваться только для определенных видов задач.  
  
## <a name="see-also"></a>См. также  
 [Представление использования](../profiling/utilization-view.md)