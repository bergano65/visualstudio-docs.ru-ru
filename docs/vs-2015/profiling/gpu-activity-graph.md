---
title: Граф активности GPU | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769051"
---
# <a name="gpu-activity-graph"></a>Граф активности GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Граф активности GPU в визуализаторе параллелизма отображает уровень активности DirectX в системе, измеренный по числу ядер DirectX, которые используются в динамике по времени.  Граф не показывает, какие конкретные ядра были использованы.  Ядро считается используемым, если оно выполняет какую-либо работу графического процессора.  
  
## <a name="gpu-activity-graph-colors"></a>Цвета на графе активности GPU  
 Зеленый цвет обозначает потребление ядер DirectX текущим процессом.  
  
 Светло-серый цвет обозначает потребление ядер DirectX другими процессами в системе. Чтобы уменьшить потребление ядер DirectX другими процессами, сократите число других процессов, выполняющихся в системе.  
  
 Белый цвет указывает на наличие неиспользуемых ядер DirectX в системе. Эти ядра доступны для процесса, если вам удастся найти дополнительные возможности для их использования. Некоторые ядра могут использоваться только для определенных видов задач.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление использования](../profiling/utilization-view.md)
