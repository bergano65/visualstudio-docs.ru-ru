---
title: Общие сведения о значениях данных по состязаниям за ресурсы | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10c06805db7ef817421f7c9f85e316af8d4b5b35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562577"
---
# <a name="understanding-resource-contention-data-values"></a>Общие сведения о значениях данных по конфликтам ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [основные сведения о значениях данных по конфликтам ресурсов](https://docs.microsoft.com/visualstudio/profiling/understanding-resource-contention-data-values).  
  
При профилировании состязаний за ресурсы происходит сбор подробных данных стека вызовов всякий раз, когда конкурирующие потоки в приложении вынуждены ожидать доступа к общему ресурсу.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 В отчетах о состязании за ресурсы содержится общее число состязаний и общее время, затраченное на ожидание ресурса модулями, функциями, строками исходного кода и инструкциями.  
  
-   Инклюзивные значения позволяют определить общее число состязаний, ставших причиной ожидания в функции, для каждого состязания за ресурс, а также общее время ожидания.  В инклюзивных значениях учитываются состязания, которые были вызваны дочерними функциями, вызванными данной функцией.  
  
-   Эксклюзивные значения позволяют определить только общее число состязаний, ставших причиной ожидания в функции и вызванных кодом в ее теле. Состязания, вызванные дочерними функциями, не включаются. Эксклюзивное время функции также включает только время ожидания, вызванного операторами в теле функции.  
  
 Кроме того, в представлениях отчета о состязаниях за ресурсы содержатся графы временной шкалы, на которых показаны отдельные события состязания в течение времени, а также стеки вызовов, создавшие определенное событие. Дополнительные сведения см. в одном из следующих разделов.  
  
-   [Представление "Сведения о потоке"](../profiling/thread-details-view-contention-data.md)  
  
-   [Представление "Сведения о ресурсах"](../profiling/resource-details-view-contention-data.md)  
  
 Дополнительные сведения о втором режиме профилирования параллелизма см. в разделе [Визуализатор параллелизма](../profiling/concurrency-visualizer.md).



