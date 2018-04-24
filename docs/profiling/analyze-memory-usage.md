---
title: Анализ использования памяти в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f29251a7b8f5e38e5b74a6aabd17ae0ccfec7651
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-memory-usage"></a>Анализ использования памяти
С помощью встроенного в отладчик средства диагностики **Использование памяти** вы сможете находить утечки памяти и выявлять ее неэффективное использование. С помощью средства "Использование памяти" можно сделать один или несколько *снимков* управляемой и собственной памяти в куче. Вы можете делать снимки приложений .NET, приложений на основе машинного кода, а также смешанных программ (на основе .NET и машинного кода).  
  
-   Можно проанализировать один мгновенный снимок, чтобы понять относительное влияние типов объектов на использование памяти и найти код в приложении, который использует память неэффективно.  
  
-   Вы также можете сравнить (diff) два мгновенных снимка приложения, чтобы найти области в коде, вызывающие рост объема используемой памяти.  

Подробные инструкции см. в учебнике [Анализ использования памяти](../profiling/memory-usage.md). Сведения об анализе использования памяти без подключения отладчика см. в статье [Использование памяти без отладчика](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Блоги и видео  

|         |         |
|---------|---------|
|  ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео")  |    [Просмотрите видео](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) об использовании средств диагностики, где показано, как можно анализировать загрузку ЦП и использование памяти в Visual Studio 2017. |

 [Анализ ресурсов ЦП и памяти во время отладки](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Блог по Visual C++. Профилирование памяти в Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>См. также
 [Профилирование в Visual Studio](../profiling/index.md)  
 [Обзор возможностей профилирования](../profiling/profiling-feature-tour.md)