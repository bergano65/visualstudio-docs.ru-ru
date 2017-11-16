---
title: "Практическое руководство. Начало и окончания сбора данных о производительности | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01870b4b687fc353c2e94d8e08ce57555cfc31f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Практическое руководство. Начало и окончания сбора данных о производительности
Прежде чем начать профилирование, необходимо добавить целевой двоичный файл, профилирование которого требуется выполнить в ходе сеанса производительности. Чтобы добавить целевой двоичный файл, щелкните правой кнопкой мыши **Целевые объекты** в **обозревателе производительности**, а затем выберите **Добавить целевой двоичный файл**. В диалоговом окне **Добавление целевого двоичного файла** выберите имя файла и нажмите кнопку **Открыть**. Будет добавлен новый двоичный файл.  
  
### <a name="to-start-profiling"></a>Запуск профилирования  
  
1.  Щелкните правой кнопкой мыши имя сеанса производительности в окне **Обозреватель производительности** и выберите один из следующих параметров.  
  
    -   **Запустить с профилированием** — запускает приложение и сразу же начинает профилирование.  
  
    -   **Запустить с приостановкой профилирования** — запускает приложение, но не начинает профилирование. Чтобы начать профилирование, выберите **Возобновить сбор** в окне **Управление сбором данных**. Дополнительные сведения см. в статье [How to: Pause and Resume Performance Data Collection](../profiling/how-to-pause-and-resume-performance-data-collection.md) (Практическое руководство. Приостановка и возобновление сбора данных о производительности).  
  
### <a name="to-end-profiling"></a>Завершение профилирования  
  
-   Рекомендуемым методом завершения сеанса профилирования является выход из приложения. Чтобы немедленно остановить профилирование, на панели инструментов **обозревателя производительности** щелкните **Остановить**.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Практическое руководство. Приостановка и возобновление сбора данных о производительности](../profiling/how-to-pause-and-resume-performance-data-collection.md)