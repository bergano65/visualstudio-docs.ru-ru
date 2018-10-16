---
title: Граф активности GPU | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90e84dbe71b529aef3cfad20172f62d65f8871d9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230208"
---
# <a name="gpu-activity-graph"></a>Граф активности GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Граф активности GPU в визуализаторе параллелизма отображает уровень активности DirectX в системе, измеренный по числу ядер DirectX, которые используются в динамике по времени.  Граф не показывает, какие конкретные ядра были использованы.  Ядро считается используемым, если оно выполняет какую-либо работу графического процессора.  
  
## <a name="gpu-activity-graph-colors"></a>Цвета на графе активности GPU  
 Зеленый цвет обозначает потребление ядер DirectX текущим процессом.  
  
 Светло-серый цвет обозначает потребление ядер DirectX другими процессами в системе. Чтобы уменьшить потребление ядер DirectX другими процессами, сократите число других процессов, выполняющихся в системе.  
  
 Белый цвет указывает на наличие неиспользуемых ядер DirectX в системе. Эти ядра доступны для процесса, если вам удастся найти дополнительные возможности для их использования. Некоторые ядра могут использоваться только для определенных видов задач.  
  
## <a name="see-also"></a>См. также  
 [Представление использования](../profiling/utilization-view.md)



